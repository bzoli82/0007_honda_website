function loadHTML(id, file) {
  fetch(file)
    .then((response) => {
      if (!response.ok) throw new Error("HTML load error");
      return response.text();
    })
    .then((data) => {
      document.getElementById(id).innerHTML = data;
    })
    .catch((error) => console.error(error));
}

loadHTML("site-header", "../includes/header.html");
loadHTML("site-footer", "../includes/footer.html");

document.addEventListener("DOMContentLoaded", function () {
  fetch("../includes/header.html")
    .then((response) => response.text())
    .then((data) => {
      const header = document.getElementById("site-header");
      header.innerHTML = data;

      // Sticky és blur beállítása
      header.style.position = "sticky";
      header.style.top = "0";
      header.style.width = "100%";
      header.style.zIndex = "1000";

      // Kritikus: átlátszó háttér és blur
      header.style.backgroundColor = "rgba(255, 255, 255, 0.6)";
      header.style.backdropFilter = "blur(10px)";
      header.style.webkitBackdropFilter = "blur(10px)";
    });
});
