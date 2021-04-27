# Time Series Analysis: Detecting Anomalies in Turbidity of New York Drinking Water
![R](https://img.shields.io/badge/Made%20With-R-yellow?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgdmlld0JveD0iMCAwIDY0IDY0IiB3aWR0aD0iNTEyIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxwYXRoIGQ9Ik0zOC4zNCA0OC43M2wzLjA0IDQuODdjLTIuOTQuOTEtNi4xIDEuNC05LjM4IDEuNHYtNi4xMmEyNS42OCAyNS42OCAwIDAwNi4zMy0uMTV6IiBmaWxsPSIjODM2MGY0Ii8+PHBhdGggZD0iTTYxIDI5YzAgOC45LTQuOTkgMTYuNzYtMTIuNiAyMS40NGwtMS40OS0yLjM4Yy0uMzQtLjU0LS43MS0xLjA2LTEuMTEtMS41NiA2LjctMy4yIDExLjItOS4xNyAxMS4yLTE2QzU3IDIwLjI4IDQ2LjkzIDEyIDM0LjUgMTJTMTIgMjAuMjggMTIgMzAuNWMwIDcuMSA0Ljg2IDEzLjI3IDEyIDE2LjM3djcuMTJDMTEuODcgNTAuODkgMyA0MC44NyAzIDI5IDMgMTQuNjQgMTUuOTggMyAzMiAzczI5IDExLjY0IDI5IDI2eiIgZmlsbD0iIzgzNjBmNCIvPjxwYXRoIGQ9Ik00OC40IDUwLjQ0TDU1IDYxaC05bC04LjgyLTE0LjEyYTQuMDIgNC4wMiAwIDAwLTMuNC0xLjg4SDMydjE1YTEgMSAwIDAxLTEgMWgtNmExIDEgMCAwMS0xLTFWMjBhMSAxIDAgMDExLTFoMTdhMTEgMTEgMCAwMTExIDExdjJhMTAuOTcgMTAuOTcgMCAwMS0xMSAxMSAxNi42NyAxNi42NyAwIDAxNC45MSA1LjA2ek00NSAzMmE1LjAyIDUuMDIgMCAwMC01LTVoLTh2MTBoOGE1IDUgMCAwMDUtNXoiIGZpbGw9IiM2NTk5ZWQiLz48ZyBmaWxsPSIjMWExYTFhIj48cGF0aCBkPSJNNDYgMzJhNiA2IDAgMDAtNi02aC04YTEgMSAwIDAwLTEgMXYxMGExIDEgMCAwMDEgMWg4YTYgNiAwIDAwNi02em0tNiA0aC03di04aDdhNCA0IDAgMDEwIDh6Ii8+PHBhdGggZD0iTTMyIDJDMTUuNDYgMiAyIDE0LjExIDIgMjljMCAxMS43NyA4LjYgMjIuMjQgMjEgMjUuNzRWNjBjMCAxLjEuOSAyIDIgMmg2YTIgMiAwIDAwMi0ydi00LjA0YTMyLjYgMzIuNiAwIDAwNy45Mi0xLjJsNC4yMyA2Ljc3Yy4xOC4zLjUuNDcuODUuNDdoOWExIDEgMCAwMC44NS0xLjUzbC02LjA4LTkuNzNDNTcuNDQgNDUuNjYgNjIgMzcuNiA2MiAyOSA2MiAxNC4xMSA0OC41NCAyIDMyIDJ6bS05IDE4djI1LjI5Yy02LjItMy4yLTEwLTguNzUtMTAtMTQuNzlDMTMgMjAuODUgMjIuNjQgMTMgMzQuNSAxM1M1NiAyMC44NSA1NiAzMC41YzAgNS45Ni0zLjggMTEuNTQtOS45NSAxNC43NC0uNDYtLjUzLS45Ni0xLjA0LTEuNDgtMS41MkExMi4wMiAxMi4wMiAwIDAwNTQgMzJ2LTJjMC02LjYyLTUuMzgtMTItMTItMTJIMjVhMiAyIDAgMDAtMiAyem0xMCAzMy45NnYtNGEyNi42OCAyNi42OCAwIDAwNC44MS0uMTdsMiAzLjJjLTIuMi41Ny00LjQ5LjktNi44MS45N3ptMC02LjAyVjQ2aC43OGMxLjA0IDAgMiAuNTMgMi41NSAxLjQxbC4zMS41Yy0xLjIuMS0yLjQzLjEtMy42NC4wM3pNNDYuNTUgNjBsLTguNTMtMTMuNjVBNC45NyA0Ljk3IDAgMDAzMy43OCA0NEgzMmExIDEgMCAwMC0xIDF2MTVoLTZWMjBoMTdjNS41MSAwIDEwIDQuNDkgMTAgMTB2MmMwIDUuNTEtNC40OSAxMC0xMCAxMGExIDEgMCAwMC0uNTUgMS44MyAxNS42NCAxNS42NCAwIDAxNC42MSA0Ljc2TDUzLjIgNjB6bTIuMTYtMTAuOTZsLS45NS0xLjUxLS40Ni0uNjhDNTMuOTMgNDMuMjcgNTggMzcuMTEgNTggMzAuNSA1OCAxOS43NSA0Ny40NiAxMSAzNC41IDExUzExIDE5Ljc1IDExIDMwLjVjMCA3LjEgNC41OCAxMy41NSAxMiAxN3Y1LjE1QzExLjc2IDQ5LjI1IDQgMzkuNyA0IDI5IDQgMTUuMjEgMTYuNTYgNCAzMiA0czI4IDExLjIxIDI4IDI1YzAgNy45Mi00LjIgMTUuMzMtMTEuMyAyMC4wNHoiLz48L2c+PC9zdmc+)
![Outlier](https://img.shields.io/badge/Time%20Series-Anomalies-9cf?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0ODAuMTggNDgwLjE4Ij48cGF0aCBkPSJNMjAwLjE4IDMyLjFjLTkyLjc4IDAtMTY4IDc1LjIyLTE2OCAxNjhzNzUuMjIgMTY4IDE2OCAxNjggMTY4LTc1LjIxIDE2OC0xNjhjLS4xLTkyLjc0LTc1LjI2LTE2Ny45LTE2OC0xNjh6bTAgMTZhMTUxLjg0IDE1MS44NCAwIDAxMTI0LjEzIDY0LjU3bC0yMCAyMGEzMS41NyAzMS41NyAwIDAwLTE2LjEzLTQuNTYgMzIgMzIgMCAwMC0zMiAzMmMuMDMgNS43IDEuNiAxMS4yNyA0LjU0IDE2LjE1bC01Mi4zOSA1Mi4zOGEzMS4wMyAzMS4wMyAwIDAwLTMyLjMgMGwtMzYuMzgtMzYuMzhhMzEuNTcgMzEuNTcgMCAwMDQuNTMtMTYuMTUgMzEuOTQgMzEuOTQgMCAwMC02Mi44Ni04SDUxLjY0YTE1Mi4yMiAxNTIuMjIgMCAwMTE0OC41NC0xMjB6bTEwNCAxMTJhMTYgMTYgMCAxMS0zMiAwIDE2IDE2IDAgMDEzMiAwem0tOTYgOTZhMTYgMTYgMCAxMS0zMiAwIDE2IDE2IDAgMDEzMiAwem0tODAtODBhMTYgMTYgMCAxMS0zMiAwIDE2IDE2IDAgMDEzMiAwem0xNDUuODYgMTU2LjkxYTE1MS44NiAxNTEuODYgMCAwMS03My44NiAxOS4xYy04My44OS4wNS0xNTEuOTQtNjcuOS0xNTItMTUxLjggMC01LjQxLjI4LTEwLjgyLjg2LTE2LjJoMzIuMjhhMzIgMzIgMCAwMDMwLjg2IDI0YzUuNy0uMDMgMTEuMjgtMS42IDE2LjE1LTQuNTRsMzYuMzkgMzYuMzhhMzEuNTcgMzEuNTcgMCAwMC00LjU0IDE2LjE2IDMyIDMyIDAgMDA2NCAwIDMxLjU3IDMxLjU3IDAgMDAtNC41My0xNi4xNmw1Mi4zOC01Mi4zOGEzMS41NyAzMS41NyAwIDAwMTYuMTUgNC41NCAzMiAzMiAwIDAwMzItMzIgMzEuNTcgMzEuNTcgMCAwMC00LjUzLTE2LjE2bDE3LjQ0LTE3LjQzYzQwLjcxIDczLjMzIDE0LjI3IDE2NS43OC01OS4wNSAyMDYuNXoiLz48cGF0aCBkPSJNNDAwLjE4IDgwLjFhMzIgMzIgMCAwMDMwLjg3LTI0aDQ5LjEzdi0xNmgtNDkuMTNhMzIgMzIgMCAwMC0zMC44Ny0yNCAzMiAzMiAwIDAwLTMyIDMyYy4wMyA1LjcgMS42IDExLjI4IDQuNTQgMTYuMTZMMzU4LjY2IDc4LjNDMjkxLjQxLTkuMyAxNjUuODYtMjUuODIgNzguMjMgNDEuNDRTLTI1LjkgMjM0LjI0IDQxLjM2IDMyMS44N2M2My40OCA4Mi43IDE3OS44NSAxMDIuNzcgMjY3LjM3IDQ2LjFsMjQuMTQgMjQuMTQgMTEuMzEgMTEuMyA2NC40IDY0LjRhNDEuOTQgNDEuOTQgMCAxMDU5LjMxLTU5LjNsLTY0LjQtNjQuNC0xMS4zLTExLjMyLTI0LjE1LTI0LjE0YTE5OS4zNCAxOTkuMzQgMCAwMDAtMjE3LjA5bDE2LTE2YTMxLjU4IDMxLjU4IDAgMDAxNi4xNCA0LjU1em0wLTQ4YTE2IDE2IDAgMTEwIDMyIDE2IDE2IDAgMDEwLTMyem01Ni40IDM4Ny43MmEyNS45NCAyNS45NCAwIDExLTM2LjY5IDM2LjY5bC02NC40LTY0LjQgMzYuNy0zNi43IDY0LjQgNjQuNHptLTc1LjcxLTc1LjcxbC0zNi42OSAzNi42OC0yMi4xNC0yMi4xNGMxLjEzLS44NiAyLjE4LTEuODIgMy4zLTIuN3MyLjQtMS45NiAzLjU5LTIuOTZjMS43NS0xLjQ3IDMuNDgtMi45NiA1LjE3LTQuNDguODctLjggMS43LTEuNiAyLjU2LTIuNGEyMDUuOCAyMDUuOCAwIDAwOS41My05LjUzYy44LS44NiAxLjYtMS42OSAyLjQtMi41NmExOTguMDUgMTk4LjA1IDAgMDA3LjQ0LTguNzdjLjg4LTEuMSAxLjgzLTIuMTYgMi43LTMuMjlsMjIuMTQgMjIuMTV6bS0zMS4wMi0zNy4xNmExODYuNzMgMTg2LjczIDAgMDEtNy44NyAxMC4yOGMtLjguOTctMS42NSAxLjktMi40OCAyLjg2YTE4MC4yMyAxODAuMjMgMCAwMS0xOS4zMyAxOS4zNGMtLjk2LjgtMS45IDEuNjctMi44NiAyLjQ4YTE4Ni43MyAxODYuNzMgMCAwMS0xMC4yOSA3Ljg2Yy04Mi44MSA1OS4xNy0xOTcuOTEgNDAtMjU3LjA4LTQyLjgyUzkuOTUgMTA5LjAzIDkyLjc3IDQ5Ljg3czE5Ny45MS00MCAyNTcuMDggNDIuODJhMTg0LjI5IDE4NC4yOSAwIDAxMCAyMTQuMjZ6Ii8+PC9zdmc+)













<div>R icon made by <a href="https://www.flaticon.com/authors/becris" title="Becris">Becris</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
