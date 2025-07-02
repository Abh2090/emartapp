FROM node:iron-bookworm AS web-build
WORKDIR /usr/src/app
COPY ..client/ ./client
RUN cd client && npm install && npm run build --prod

# Use official nginx image as the base image
FROM nginx:stable-perl

# Copy the build output to replace the default nginx contents.
COPY --from=web-build /usr/src/app/client/dist/client/ /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 4200
EXPOSE 4200
