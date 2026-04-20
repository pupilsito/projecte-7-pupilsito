# 2. Codigo PlantUML y imagen del diagrama de Gantt
```js
@startgantt
Project starts the 2026-05-06
saturday are closed
sunday are closed

[T01 - Competencia i Sector] lasts 2 days

[T02 - Web corporativa] lasts 3 days
[T02 - Web corporativa] starts at [T01 - Competencia i Sector]'s end

[T03 - Servidor de fitxers] lasts 4 days
[T03 - Servidor de fitxers] starts at [T02 - Web corporativa]'s end

[T04 - Servidor d'impressio] lasts 2 days
[T04 - Servidor d'impressio] starts at [T03 - Servidor de fitxers]'s end

[T05 - Videos LOPD] lasts 4 days
[T05 - Videos LOPD] starts at [T01 - Competencia i Sector]'s end

[T06 - Adaptacio legal web] lasts 3 days
[T06 - Adaptacio legal web] starts at [T02 - Web corporativa]'s end

[T07 - Integracio final] lasts 2 days
[T07 - Integracio final] starts at [T04 - Servidor d'impressio]'s end
[T07 - Integracio final] starts at [T06 - Adaptacio legal web]'s end

[T08 - Informe final i presentacio] lasts 3 days
[T08 - Informe final i presentacio] starts at [T07 - Integracio final]'s end

@endgantt
```