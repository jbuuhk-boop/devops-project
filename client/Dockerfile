FROM node:22-alpine AS build

ARG VITE_SERVER_URL=http://backend:5000
ENV VITE_SERVER_URL=$VITE_SERVER_URL

WORKDIR /client

COPY . .

RUN npm install

RUN npm run build


FROM nginx:alpine

COPY --from=build /client/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
