# Time Series Analysis: Detecting Anomalies in Turbidity of New York Drinking Water
![R](https://img.shields.io/badge/Made%20With-R-yellow?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgdmlld0JveD0iMCAwIDY0IDY0IiB3aWR0aD0iNTEyIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxwYXRoIGQ9Ik0zOC4zNCA0OC43M2wzLjA0IDQuODdjLTIuOTQuOTEtNi4xIDEuNC05LjM4IDEuNHYtNi4xMmEyNS42OCAyNS42OCAwIDAwNi4zMy0uMTV6IiBmaWxsPSIjODM2MGY0Ii8+PHBhdGggZD0iTTYxIDI5YzAgOC45LTQuOTkgMTYuNzYtMTIuNiAyMS40NGwtMS40OS0yLjM4Yy0uMzQtLjU0LS43MS0xLjA2LTEuMTEtMS41NiA2LjctMy4yIDExLjItOS4xNyAxMS4yLTE2QzU3IDIwLjI4IDQ2LjkzIDEyIDM0LjUgMTJTMTIgMjAuMjggMTIgMzAuNWMwIDcuMSA0Ljg2IDEzLjI3IDEyIDE2LjM3djcuMTJDMTEuODcgNTAuODkgMyA0MC44NyAzIDI5IDMgMTQuNjQgMTUuOTggMyAzMiAzczI5IDExLjY0IDI5IDI2eiIgZmlsbD0iIzgzNjBmNCIvPjxwYXRoIGQ9Ik00OC40IDUwLjQ0TDU1IDYxaC05bC04LjgyLTE0LjEyYTQuMDIgNC4wMiAwIDAwLTMuNC0xLjg4SDMydjE1YTEgMSAwIDAxLTEgMWgtNmExIDEgMCAwMS0xLTFWMjBhMSAxIDAgMDExLTFoMTdhMTEgMTEgMCAwMTExIDExdjJhMTAuOTcgMTAuOTcgMCAwMS0xMSAxMSAxNi42NyAxNi42NyAwIDAxNC45MSA1LjA2ek00NSAzMmE1LjAyIDUuMDIgMCAwMC01LTVoLTh2MTBoOGE1IDUgMCAwMDUtNXoiIGZpbGw9IiM2NTk5ZWQiLz48ZyBmaWxsPSIjMWExYTFhIj48cGF0aCBkPSJNNDYgMzJhNiA2IDAgMDAtNi02aC04YTEgMSAwIDAwLTEgMXYxMGExIDEgMCAwMDEgMWg4YTYgNiAwIDAwNi02em0tNiA0aC03di04aDdhNCA0IDAgMDEwIDh6Ii8+PHBhdGggZD0iTTMyIDJDMTUuNDYgMiAyIDE0LjExIDIgMjljMCAxMS43NyA4LjYgMjIuMjQgMjEgMjUuNzRWNjBjMCAxLjEuOSAyIDIgMmg2YTIgMiAwIDAwMi0ydi00LjA0YTMyLjYgMzIuNiAwIDAwNy45Mi0xLjJsNC4yMyA2Ljc3Yy4xOC4zLjUuNDcuODUuNDdoOWExIDEgMCAwMC44NS0xLjUzbC02LjA4LTkuNzNDNTcuNDQgNDUuNjYgNjIgMzcuNiA2MiAyOSA2MiAxNC4xMSA0OC41NCAyIDMyIDJ6bS05IDE4djI1LjI5Yy02LjItMy4yLTEwLTguNzUtMTAtMTQuNzlDMTMgMjAuODUgMjIuNjQgMTMgMzQuNSAxM1M1NiAyMC44NSA1NiAzMC41YzAgNS45Ni0zLjggMTEuNTQtOS45NSAxNC43NC0uNDYtLjUzLS45Ni0xLjA0LTEuNDgtMS41MkExMi4wMiAxMi4wMiAwIDAwNTQgMzJ2LTJjMC02LjYyLTUuMzgtMTItMTItMTJIMjVhMiAyIDAgMDAtMiAyem0xMCAzMy45NnYtNGEyNi42OCAyNi42OCAwIDAwNC44MS0uMTdsMiAzLjJjLTIuMi41Ny00LjQ5LjktNi44MS45N3ptMC02LjAyVjQ2aC43OGMxLjA0IDAgMiAuNTMgMi41NSAxLjQxbC4zMS41Yy0xLjIuMS0yLjQzLjEtMy42NC4wM3pNNDYuNTUgNjBsLTguNTMtMTMuNjVBNC45NyA0Ljk3IDAgMDAzMy43OCA0NEgzMmExIDEgMCAwMC0xIDF2MTVoLTZWMjBoMTdjNS41MSAwIDEwIDQuNDkgMTAgMTB2MmMwIDUuNTEtNC40OSAxMC0xMCAxMGExIDEgMCAwMC0uNTUgMS44MyAxNS42NCAxNS42NCAwIDAxNC42MSA0Ljc2TDUzLjIgNjB6bTIuMTYtMTAuOTZsLS45NS0xLjUxLS40Ni0uNjhDNTMuOTMgNDMuMjcgNTggMzcuMTEgNTggMzAuNSA1OCAxOS43NSA0Ny40NiAxMSAzNC41IDExUzExIDE5Ljc1IDExIDMwLjVjMCA3LjEgNC41OCAxMy41NSAxMiAxN3Y1LjE1QzExLjc2IDQ5LjI1IDQgMzkuNyA0IDI5IDQgMTUuMjEgMTYuNTYgNCAzMiA0czI4IDExLjIxIDI4IDI1YzAgNy45Mi00LjIgMTUuMzMtMTEuMyAyMC4wNHoiLz48L2c+PC9zdmc+)
![Outlier](https://img.shields.io/badge/Anomalies-Deetection-9cf?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMiA5OCA5OCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiPjxsaW5lYXJHcmFkaWVudCBpZD0iYSIgZ3JhZGllbnRVbml0cz0idXNlclNwYWNlT25Vc2UiIHgxPSIyNi4xNSIgeTE9IjcuMjUiIHgyPSIyNi4xNSIgeTI9Ijk0LjUxIj48c3RvcCBvZmZzZXQ9IjAiIHN0b3AtY29sb3I9IiMwMGVmZDEiLz48c3RvcCBvZmZzZXQ9IjEiIHN0b3AtY29sb3I9IiMwMGFjZWEiLz48L2xpbmVhckdyYWRpZW50PjxwYXRoIGQ9Ik0yNi42IDI4LjhjLTQuMyA0LjMtNi41IDEwLjQtNS45IDE2LjZhMy4xIDMuMSAwIDAwMyAyLjdoLjNjMS42LS4yIDIuOS0xLjYgMi43LTMuMy0uNC00LjQgMS4xLTguNyA0LjEtMTEuOGEyLjkgMi45IDAgMDAwLTQuMmMtMS4yLTEtMy0xLjEtNC4yIDB6IiBmaWxsPSJ1cmwoI2EpIi8+PGxpbmVhckdyYWRpZW50IGlkPSJiIiBncmFkaWVudFVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgeDE9IjQ5IiB5MT0iNy4yNSIgeDI9IjQ5IiB5Mj0iOTQuNTEiPjxzdG9wIG9mZnNldD0iMCIgc3RvcC1jb2xvcj0iIzAwZWZkMSIvPjxzdG9wIG9mZnNldD0iMSIgc3RvcC1jb2xvcj0iIzAwYWNlYSIvPjwvbGluZWFyR3JhZGllbnQ+PHBhdGggZD0iTTg4LjcgODYuNUw2OSA2Ni43YzUtNiA4LTEzLjYgOC0yMiAwLTE4LjktMTUuNC0zNC4zLTM0LjMtMzQuM1M4LjQgMjUuOCA4LjQgNDQuN0M4LjQgNjMuNSAyMy44IDc5IDQyLjcgNzljOC40IDAgMTYuMS0zIDIyLThsMTkuOCAxOS44Yy42LjYgMS40LjkgMi4xLjkuNyAwIDEuNS0uMyAyLjEtLjkgMS4yLTEuMyAxLjItMy4zIDAtNC4zem0tMjUuOC0yMmwtLjIuMi0uMi4yYy01LjEgNS0xMi4xIDguMS0xOS44IDguMS0xNS42IDAtMjguMy0xMi43LTI4LjMtMjguMyAwLTE1LjYgMTIuNy0yOC4zIDI4LjMtMjguM0M1OC4zIDE2LjMgNzEgMjkgNzEgNDQuN2MwIDcuNi0zLjEgMTQuNi04LjEgMTkuOHoiIGZpbGw9InVybCgjYikiLz48L3N2Zz4=)
![Time](https://img.shields.io/badge/Time%20Series-Analysis-blue?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MTEuOTkgNTExLjk5IiB3aWR0aD0iNTEyIiBoZWlnaHQ9IjUxMiI+PHBhdGggZmlsbD0iI2Q1ZjVmYiIgZD0iTTI3NS42NCA2OC4yNmg2OC40MXYzOS40OGgtNjguNDF6Ii8+PHBhdGggZD0iTTI3My44NSA2OC4yNmg3MmEyNCAyNCAwIDEwMC00OGgtNzJhMjQgMjQgMCAxMDAgNDh6IiBmaWxsPSIjZmY3NDgwIi8+PGNpcmNsZSBjeD0iMzEwIiBjeT0iMjk5Ljc0IiByPSIxOTIiIGZpbGw9IiM1ZGRlZjUiLz48Y2lyY2xlIGN4PSIzMTAiIGN5PSIyOTkuNzQiIHI9IjE0NS4xMyIgZmlsbD0iI2ZmZiIvPjxjaXJjbGUgY3g9IjMxMCIgY3k9IjI5OS43NCIgcj0iMjEuMDciIGZpbGw9IiNmZjgzOGUiLz48Zz48cGF0aCBkPSJNNTExIDI3OS42NWEyMDIuMzggMjAyLjM4IDAgMDAtNTguMTYtMTIyLjc1IDIwMC44IDIwMC44IDAgMDAtOTguNzgtNTQuMjR2LTI1LjRhMzQuMDYgMzQuMDYgMCAwMDI1Ljc5LTMzYzAtMTguNzUtMTUuMjUtMzQtMzQtMzRoLTcyYy0xOC43NSAwLTM0IDE1LjI1LTM0IDM0IDAgMTUuOTIgMTEgMjkuMzEgMjUuOCAzM3YyNS40N2EyMDAuOCAyMDAuOCAwIDAwLTk4LjQ4IDU0LjE3IDIwMi45NyAyMDIuOTcgMCAwMC0xNi45OCAxOS4yN2MtLjI2LS4wMi0uNS0uMDQtLjc2LS4wNEg3OC4xN2ExMCAxMCAwIDAwMCAyMGg1OC40YTIwMC40NyAyMDAuNDcgMCAwMC0xNy43MyAzOC40NEgxMGExMCAxMCAwIDAwMCAyMGgxMDMuMThhMjAzLjMyIDIwMy4zMiAwIDAwLTQuOTYgMzguNDRINjRhMTAgMTAgMCAwMDAgMjBoNDQuNTRhMjAzLjAyIDIwMy4wMiAwIDAwNi4yNCAzOC40M0g1MGExMCAxMCAwIDAwMCAyMGg3MS4xN2EyMDAuODMgMjAwLjgzIDAgMDA0NiA3MS4xNCAyMDIuMzcgMjAyLjM3IDAgMDAxMjIuODYgNTguMTggMjAyLjQ4IDIwMi40OCAwIDAwMTMwLjA2LTMxLjYgMTAgMTAgMCAwMC0xMC45MS0xNi43N2MtNzEuNTYgNDYuNi0xNjcuNCAzNi41Mi0yMjcuODctMjMuOTYtNzAuOTYtNzAuOTYtNzAuOTYtMTg2LjQyIDAtMjU3LjM4IDcwLjk2LTcwLjk2IDE4Ni40Mi03MC45NiAyNTcuMzggMCA2MC40IDYwLjQgNzAuNTMgMTU2LjE1IDI0LjA5IDIyNy42N2ExMCAxMCAwIDAwMTYuNzcgMTAuOUEyMDIuNjQgMjAyLjY0IDAgMDA1MTEgMjc5LjY0ek0yNTkuODYgNDQuMjZjMC03LjcyIDYuMjgtMTQgMTQtMTRoNzJjNy43MiAwIDE0IDYuMjggMTQgMTRzLTYuMjggMTQtMTQgMTRoLTcyYy03LjcyIDAtMTQtNi4yOC0xNC0xNHptMjUuOCA1NS4wNFY3OC4yNmg0OC40djIxYTIwMy43NiAyMDMuNzYgMCAwMC00OC40LjA0eiIvPjxwYXRoIGQ9Ik00NDUuNzcgNDI1LjVhMTAuMDMgMTAuMDMgMCAwMC03LjA3IDE3LjA3IDEwLjAxIDEwLjAxIDAgMDAxNy4wNy03LjA3YzAtMi42My0xLjA3LTUuMjEtMi45My03LjA3YTEwLjEgMTAuMSAwIDAwLTcuMDctMi45M3pNMzEwIDE0NC42Yy04NS41NCAwLTE1NS4xMyA2OS42LTE1NS4xMyAxNTUuMTRTMjI0LjQ3IDQ1NC44NyAzMTAgNDU0Ljg3czE1NS4xMy02OS42IDE1NS4xMy0xNTUuMTNTMzk1LjUzIDE0NC42IDMxMCAxNDQuNnptMCAyOTAuMjdjLTc0LjUxIDAtMTM1LjEzLTYwLjYyLTEzNS4xMy0xMzUuMTNTMjM1LjUgMTY0LjYgMzEwIDE2NC42czEzNS4xMyA2MC42MiAxMzUuMTMgMTM1LjEzUzM4NC41MSA0MzQuODcgMzEwIDQzNC44N3oiLz48cGF0aCBkPSJNMzczLjI2IDIyMi4zNGwtNDkuNTMgNDkuNTNhMzAuODggMzAuODggMCAwMC0yNy40NiAwbC0yMi4xNi0yMi4xN2ExMCAxMCAwIDAwLTE0LjE1IDE0LjE0bDIyLjE3IDIyLjE3YTMwLjg3IDMwLjg3IDAgMDAtMy4yIDEzLjczYzAgMTcuMTMgMTMuOTQgMzEuMDcgMzEuMDcgMzEuMDdzMzEuMDctMTMuOTQgMzEuMDctMzEuMDdjMC00LjkzLTEuMTUtOS41OS0zLjItMTMuNzNsNDguMDgtNDguMDcgMS40NS0xLjQ2YTEwIDEwIDAgMDAtMTQuMTQtMTQuMTR6TTMxMCAzMTAuODFjLTYuMSAwLTExLjA3LTQuOTctMTEuMDctMTEuMDdzNC45Ni0xMS4wOCAxMS4wNy0xMS4wOGExMS4wOCAxMS4wOCAwIDAxMCAyMi4xNXpNNDE2LjkyIDI4OS44NmgtOS4yN2ExMCAxMCAwIDAwMCAyMGg5LjI3YTEwIDEwIDAgMDAwLTIwek0yMTIuMzUgMjg5LjYyaC05LjI3YTEwIDEwIDAgMDAwIDIwaDkuMjdhMTAgMTAgMCAwMDAtMjB6TTMxMC4xMiAyMTIuMDhhMTAgMTAgMCAwMDEwLTEwdi05LjI2YTEwIDEwIDAgMDAtMjAgMHY5LjI2YTEwIDEwIDAgMDAxMCAxMHpNMzA5Ljg4IDM4Ny40YTEwIDEwIDAgMDAtMTAgMTB2OS4yNmExMCAxMCAwIDAwMjAgMHYtOS4yN2ExMCAxMCAwIDAwLTEwLTEwek0xMCAzNTEuNDRjLTIuNjMgMC01LjIxIDEuMDctNy4wNyAyLjkzQTEwLjA4IDEwLjA4IDAgMDAwIDM2MS40NGMwIDIuNjQgMS4wNyA1LjIxIDIuOTMgNy4wN3M0LjQ0IDIuOTMgNy4wNyAyLjkzIDUuMjEtMS4wNyA3LjA3LTIuOTNjMS44Ni0xLjg2IDIuOTMtNC40NCAyLjkzLTcuMDdzLTEuMDctNS4yMS0yLjkzLTcuMDdhMTAuMDcgMTAuMDcgMCAwMC03LjA3LTIuOTN6Ii8+PC9nPjwvc3ZnPg==)








<div>R icon made by <a href="https://www.flaticon.com/authors/becris" title="Becris">Becris</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
<div>Maginifying glass icon made by <a href="" title="Kiranshastry">Kiranshastry</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
