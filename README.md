# KIT-Physik-Praktikum-LaTeX-Vorlage-P3-T1-T2
Diese LaTeX-Vorlage ist geeignet für das Fortgeschrittenenpraktikum P3-T1 und das Masterpraktikum P3-T2 der Fakultät für Physik am Karlsruher Institut für Technologie. Es wird die Verwendung von Overleaf empfohlen.
Bei Fragen oder Problemen könnt ihr euch gerne an soeren@fachschaft.physik.kit.edu wenden.

## Import der Vorlage
1. Richte dir deine Arbeitsumgebung ein. Dafür kannst du gerne einen lokalen Compiler verwenden, wir empfehlen aber immer [Overleaf](https://www.overleaf.com/).
   1. Gehe auf den **Log In**-Button.
   2. Scrolle runter und klicke auf **Log in through your institution**.
   3. Tippe in das Eingabefeld deine KIT-Adresse mit dem Format `uXXXX@student.kit.edu` ein.
   4. Melde dich, wie von zum Beispiel ILIAS gewohnt, mit deinem KIT-Account an.
2. Lade dir das Projekt als ZIP-Datei über den grünen Button "Code" und dannn als "Download ZIP" herunter.
3. In **Overleaf** musst du auf **New project** klicken, dort **Upload project** auswählen und die soeben heruntergeladene ZIP-Datei dort hochladen.

## Verwendung
1. In die main.tex wird kein Inhalt geschrieben. Hier werden bei Bedarf benötigte Pakete hinzugefügt oder weitere Kapitel(Aufgaben) importiert.
2. Füllt die Datei Deckblatt.tex im Ordner chapters mit euren Daten aus.
3. Schreibt eure Vorbereitung in den Versuch unter chapters/Vorbereitung.tex. Im Inhaltsverzeichnis erhält die Versuchsvorbereitung keine Kapitelnummer um die von der Fakultät gegebenen Protokollanforderungen zu erfüllen.
4. Laut Vorgabe der Fakultät soll das erste Kapitel die theoretischen Grundlagen des Versuchs erklären. Dies fällt häufig mit der Versuchsvorbereitung zusammen. Die Versuchsvorbereitung kann in diesem Fall entfernt werden.
5. Das zweite Kapite beinhaltet den experimentellen Versuchsaufbau, das dritte die Durchführung und das vierte kapitel beinhaltet die Auswertung samt Fehlerrechnung. 
6. Anhänge wie Grafiken oder das Messprotokoll werden im Ordner include abgelegt. Es macht Sinn für jedes Kapitel einen Unterordner in include anzulegen um Ordnung zu bewahren. Somit könnt ihr die Grafiken schneller wieder finden, wenn sie ausgetauscht werden müssen.
7. Tauscht die Dateien Aufgabenblatt.pdf und Messptrotokoll.pdf durch das entsprechende Aufgabenblatt und euer eingescanntes, unterschriebenes Messprotokoll aus.

## Codeschnipsel für die wichtigsten Dinge

Hier findest du eine Auflistung an wichtigen Beispielen, die für LaTeX-Neulinge sehr hilfreich sein können.

### Bilder/Grafik einfügen

```
\begin{figure}[h] % h for here; t for top; b for bottom; ! overrides internal parameters LaTeX uses for determining "good" float positions
\centering % Zentrieren der Grafik horizontal auf der Seite
    \includegraphics{include/Foto.png} % Lade die Datei Foto.png aus dem include-Ordner
    \caption{} % Bildunterschrift
    \label{} % Label zum refenzieren mit \ref{}
\end{figure}
```

Unterstützte Dateiformate: `*.png`, `*.jpg`, `*.jpeg`, `*.pdf`

### Tabellen einfügen

```
\begin{table}[!htb] % h for here; t for top; b for bottom; ! overrides internal parameters LaTeX uses for determining "good" float positions
    \centering % Zentrieren der Tabelle auf der Seite
    \caption{} % Tabellen haben Überschriften!
    \label{} % Label zum refenzieren mit \ref{}
    \bigskip % Sorge dafür, dass die Überschrift nicht an der Tabelle klebt
     \begin{tabular}{ccc} % Tabelle mit drei Spalten mit Trennstrichen, deren Inhalte mittig zentriert sind
	\toprule
	Text & Text & Text\\ % Spaltenbezeichungen
	\midrule
	Text & Text & Text\\ % Tabelleninhalt
	\hline
	Text & Text & Text\\ % Tabelleninhalt
	\hline
	Text & Text & Text\\ % Tabelleninhalt
	\bottomrule
    \end{tabular}
\end{table}
```

Solltest du die Daten bereits in einer `*.csv`-Datei haben, so kannst du diese auch einfach mithilfe von diesem 
Code-Schnipsel aus Dateien auslesen und dir anzeigen lassen.

```
\begin{table}[]
    \centering
    \caption{} % Tabellenüberschrift
    \label{} % Label der Tabelle fürs referenzieren
    \bigskip % Stelle sicher, dass die Überschrift nicht an der Tabelle klebt
    \pgfplotstabletypeset[
        columns={Nr,Length(um),Depth(nm)}, % Spalten aus der CSV-Datei, die importiert werden sollen
        % Die folgenden Parameter geben für jede Spalte an:
        % column name={Bezeichung der Spalte}
        % precision=Anzahl der Stellen, die Zahlen in der Spalte haben sollen
        % fixed zerofill -> Fülle mit Nullen auf, sollte der Wert nicht die Länge der precision haben
        % fixed -> Runde die Zahlen auf die precision
        % column type = {r} -> Wie ist die Spalte ausgerichtet (r: rechtsbündig, l: linksbündig, c: zentriert)
        display columns/0/.style={column name={Nr.}, precision=0, fixed zerofill, column type = {r}},
        display columns/1/.style={column name={Länge $l$ ($\si{\micro\meter}$)}, precision=1, fixed, fixed zerofill, column type = {r}},
        display columns/2/.style={column name={Tiefe $t$ ($\si{nm}$)}, precision=0, fixed zerofill, column type = {r}},
        ]{Daten.csv} % Lese die Daten aus der Daten.csv-Datei aus
\end{table}
```

### Referenzierung
Die Referenzierung von Objekten ist recht einfach. Dafür muss an der Stelle, die referenziert werden soll, ein
`\label{Beispielname}` erstellt werden, um dann mit `\ref{Beispielname}` darauf verweisen zu können. Dabei gilt,
dass jeder Name nur einmal mit dem `\label`-Befehl definiert werden darf, denn sonst kann LaTeX die Referenz nicht mehr 
eindeutig identifizieren.

```
Dies ist ein Beispieltext, der auf ein Beispielbild in Abbildung \ref{Beispielname} zeigt.
```

### Formeln

```
\begin{equation} % equation Umgebung wird für einzeilige Gleichungen verwendet
  a^2 + b^2 = c^2
  \label{} % Label zum refenzieren mit \ref{}
\end{equation}
```

Die align Umgebung wird für mehrzeilige Gleichungen verwendet. Die Gleichungen werden am Gleichheitszeichen (&=) ausgerichtet  
```
\begin{align}
  a^2 + b^2 &= c^2\\
  c^2 &= a^2 + b^2
  \label{} % Label zum refenzieren mit \ref{}
\end{align}
```

Eine relativ ausführliche Übersicht der verfügbaren Zeichen kann
[hier](https://de.wikipedia.org/wiki/Liste_mathematischer_Symbole) gefunden werden.

### Wertangabe

Entweder:
```
\begin{equation}
  \mathrm{Name} = \SI{Wert}{Einheit}
\end{equation}
```

oder
```
\begin{equation}
  \mathrm{Name} = Wert\,\mathrm{Einheit}
\end{equation}
```

#### Fehler-Rechnung Wertangabe:
Die Angabe von Ergebnissen der Fehlerrechnung erfolgt nach dem Schema:
> Ergebnis = Messwert +/- statistischer Fehler +/- systematischer Fehler

```
\begin{equation}
  \mathrm{Name} = Wert \pm Wert \mathrm{(\delta_{stat})} \pm Wert \mathrm{(\delta_{sys})}\mathrm{Einheit}
\end{equation}
```

### Fußnote

Kann im Text eingebaut werden. Eine Fußnote erscheint im Text. Der Inhalt erscheint im Footer der Seite

```
\footnote{Quelle}
```

### Listen

#### Umnummerierte Listen

```
\begin{itemize}
\item Listenpunkt 1
\item Listenpunkt 2
\end{itemize}
```

#### Nummerierte Listen
```
\begin{enumerate} 
    \item Ein Stichpunkt
    \item Noch ein Stichpunkt 
\end{enumerate}
```