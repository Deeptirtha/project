# project


const fs=require("fs")
const http = require("http");
const { Http2ServerRequest } = require("http2");

// console.log(http);

const requestHandler = (request, response) => {
//   console.log(request.url);
  const { url } = request;
  if (url === "/" && request.method == "GET") {
    response.write("<h1>Homepageee</h1>");
    response.end();
    return;
  }
  if (url === "/courses") {
    response.write("<h1>Courses & all  <a href='/'>Go To HOME</a></h1>");
    response.end();
    return;
  }
  if (url === "/student"  && request.method == "GET") {
    response.write("<h1>student  <a href='/courses'>Go To courses</a></h1>");
    response.end();
  }
  if (url === "/abc"  && request.method == "GET") {
    response.write(fs.readFileSync("bio.txt").toString());
    response.end();
  }
};

const server = http.createServer(requestHandler);
server.listen(3000);
