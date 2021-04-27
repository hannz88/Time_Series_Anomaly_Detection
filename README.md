# Time Series Analysis: Detecting Anomalies in Turbidity of New York Drinking Water
![R](https://img.shields.io/badge/Made%20With-R-yellow?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgdmlld0JveD0iMCAwIDY0IDY0IiB3aWR0aD0iNTEyIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxwYXRoIGQ9Ik0zOC4zNCA0OC43M2wzLjA0IDQuODdjLTIuOTQuOTEtNi4xIDEuNC05LjM4IDEuNHYtNi4xMmEyNS42OCAyNS42OCAwIDAwNi4zMy0uMTV6IiBmaWxsPSIjODM2MGY0Ii8+PHBhdGggZD0iTTYxIDI5YzAgOC45LTQuOTkgMTYuNzYtMTIuNiAyMS40NGwtMS40OS0yLjM4Yy0uMzQtLjU0LS43MS0xLjA2LTEuMTEtMS41NiA2LjctMy4yIDExLjItOS4xNyAxMS4yLTE2QzU3IDIwLjI4IDQ2LjkzIDEyIDM0LjUgMTJTMTIgMjAuMjggMTIgMzAuNWMwIDcuMSA0Ljg2IDEzLjI3IDEyIDE2LjM3djcuMTJDMTEuODcgNTAuODkgMyA0MC44NyAzIDI5IDMgMTQuNjQgMTUuOTggMyAzMiAzczI5IDExLjY0IDI5IDI2eiIgZmlsbD0iIzgzNjBmNCIvPjxwYXRoIGQ9Ik00OC40IDUwLjQ0TDU1IDYxaC05bC04LjgyLTE0LjEyYTQuMDIgNC4wMiAwIDAwLTMuNC0xLjg4SDMydjE1YTEgMSAwIDAxLTEgMWgtNmExIDEgMCAwMS0xLTFWMjBhMSAxIDAgMDExLTFoMTdhMTEgMTEgMCAwMTExIDExdjJhMTAuOTcgMTAuOTcgMCAwMS0xMSAxMSAxNi42NyAxNi42NyAwIDAxNC45MSA1LjA2ek00NSAzMmE1LjAyIDUuMDIgMCAwMC01LTVoLTh2MTBoOGE1IDUgMCAwMDUtNXoiIGZpbGw9IiM2NTk5ZWQiLz48ZyBmaWxsPSIjMWExYTFhIj48cGF0aCBkPSJNNDYgMzJhNiA2IDAgMDAtNi02aC04YTEgMSAwIDAwLTEgMXYxMGExIDEgMCAwMDEgMWg4YTYgNiAwIDAwNi02em0tNiA0aC03di04aDdhNCA0IDAgMDEwIDh6Ii8+PHBhdGggZD0iTTMyIDJDMTUuNDYgMiAyIDE0LjExIDIgMjljMCAxMS43NyA4LjYgMjIuMjQgMjEgMjUuNzRWNjBjMCAxLjEuOSAyIDIgMmg2YTIgMiAwIDAwMi0ydi00LjA0YTMyLjYgMzIuNiAwIDAwNy45Mi0xLjJsNC4yMyA2Ljc3Yy4xOC4zLjUuNDcuODUuNDdoOWExIDEgMCAwMC44NS0xLjUzbC02LjA4LTkuNzNDNTcuNDQgNDUuNjYgNjIgMzcuNiA2MiAyOSA2MiAxNC4xMSA0OC41NCAyIDMyIDJ6bS05IDE4djI1LjI5Yy02LjItMy4yLTEwLTguNzUtMTAtMTQuNzlDMTMgMjAuODUgMjIuNjQgMTMgMzQuNSAxM1M1NiAyMC44NSA1NiAzMC41YzAgNS45Ni0zLjggMTEuNTQtOS45NSAxNC43NC0uNDYtLjUzLS45Ni0xLjA0LTEuNDgtMS41MkExMi4wMiAxMi4wMiAwIDAwNTQgMzJ2LTJjMC02LjYyLTUuMzgtMTItMTItMTJIMjVhMiAyIDAgMDAtMiAyem0xMCAzMy45NnYtNGEyNi42OCAyNi42OCAwIDAwNC44MS0uMTdsMiAzLjJjLTIuMi41Ny00LjQ5LjktNi44MS45N3ptMC02LjAyVjQ2aC43OGMxLjA0IDAgMiAuNTMgMi41NSAxLjQxbC4zMS41Yy0xLjIuMS0yLjQzLjEtMy42NC4wM3pNNDYuNTUgNjBsLTguNTMtMTMuNjVBNC45NyA0Ljk3IDAgMDAzMy43OCA0NEgzMmExIDEgMCAwMC0xIDF2MTVoLTZWMjBoMTdjNS41MSAwIDEwIDQuNDkgMTAgMTB2MmMwIDUuNTEtNC40OSAxMC0xMCAxMGExIDEgMCAwMC0uNTUgMS44MyAxNS42NCAxNS42NCAwIDAxNC42MSA0Ljc2TDUzLjIgNjB6bTIuMTYtMTAuOTZsLS45NS0xLjUxLS40Ni0uNjhDNTMuOTMgNDMuMjcgNTggMzcuMTEgNTggMzAuNSA1OCAxOS43NSA0Ny40NiAxMSAzNC41IDExUzExIDE5Ljc1IDExIDMwLjVjMCA3LjEgNC41OCAxMy41NSAxMiAxN3Y1LjE1QzExLjc2IDQ5LjI1IDQgMzkuNyA0IDI5IDQgMTUuMjEgMTYuNTYgNCAzMiA0czI4IDExLjIxIDI4IDI1YzAgNy45Mi00LjIgMTUuMzMtMTEuMyAyMC4wNHoiLz48L2c+PC9zdmc+)
![Outlier](https://img.shields.io/badge/Anomalies-Deetection-9cf?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMiA5OCA5OCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiPjxsaW5lYXJHcmFkaWVudCBpZD0iYSIgZ3JhZGllbnRVbml0cz0idXNlclNwYWNlT25Vc2UiIHgxPSIyNi4xNSIgeTE9IjcuMjUiIHgyPSIyNi4xNSIgeTI9Ijk0LjUxIj48c3RvcCBvZmZzZXQ9IjAiIHN0b3AtY29sb3I9IiMwMGVmZDEiLz48c3RvcCBvZmZzZXQ9IjEiIHN0b3AtY29sb3I9IiMwMGFjZWEiLz48L2xpbmVhckdyYWRpZW50PjxwYXRoIGQ9Ik0yNi42IDI4LjhjLTQuMyA0LjMtNi41IDEwLjQtNS45IDE2LjZhMy4xIDMuMSAwIDAwMyAyLjdoLjNjMS42LS4yIDIuOS0xLjYgMi43LTMuMy0uNC00LjQgMS4xLTguNyA0LjEtMTEuOGEyLjkgMi45IDAgMDAwLTQuMmMtMS4yLTEtMy0xLjEtNC4yIDB6IiBmaWxsPSJ1cmwoI2EpIi8+PGxpbmVhckdyYWRpZW50IGlkPSJiIiBncmFkaWVudFVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgeDE9IjQ5IiB5MT0iNy4yNSIgeDI9IjQ5IiB5Mj0iOTQuNTEiPjxzdG9wIG9mZnNldD0iMCIgc3RvcC1jb2xvcj0iIzAwZWZkMSIvPjxzdG9wIG9mZnNldD0iMSIgc3RvcC1jb2xvcj0iIzAwYWNlYSIvPjwvbGluZWFyR3JhZGllbnQ+PHBhdGggZD0iTTg4LjcgODYuNUw2OSA2Ni43YzUtNiA4LTEzLjYgOC0yMiAwLTE4LjktMTUuNC0zNC4zLTM0LjMtMzQuM1M4LjQgMjUuOCA4LjQgNDQuN0M4LjQgNjMuNSAyMy44IDc5IDQyLjcgNzljOC40IDAgMTYuMS0zIDIyLThsMTkuOCAxOS44Yy42LjYgMS40LjkgMi4xLjkuNyAwIDEuNS0uMyAyLjEtLjkgMS4yLTEuMyAxLjItMy4zIDAtNC4zem0tMjUuOC0yMmwtLjIuMi0uMi4yYy01LjEgNS0xMi4xIDguMS0xOS44IDguMS0xNS42IDAtMjguMy0xMi43LTI4LjMtMjguMyAwLTE1LjYgMTIuNy0yOC4zIDI4LjMtMjguM0M1OC4zIDE2LjMgNzEgMjkgNzEgNDQuN2MwIDcuNi0zLjEgMTQuNi04LjEgMTkuOHoiIGZpbGw9InVybCgjYikiLz48L3N2Zz4=)











<div>R icon made by <a href="https://www.flaticon.com/authors/becris" title="Becris">Becris</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
<div>Magnifying glass icon made by <a href="https://www.flaticon.com/authors/mynamepong" title="mynamepong">mynamepong</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
