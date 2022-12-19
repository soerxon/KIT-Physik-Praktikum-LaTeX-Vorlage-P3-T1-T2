# KIT-Physik-Praktikum-LaTeX-Vorlage-P3-T1-T2
Diese LaTeX-Vorlage ist geeignet für das Fortgeschrittenenpraktikum P3-T1 und das Masterpraktikum P3-T2 der Fakultät für Physik am Karlsruher Institut für Technologie. Es wird die Verwendung von Overleaf empfohlen.
Bei Fragen oder Problemen könnt ihr euch gerne an soeren@fachschaft.physik.kit.edu wenden.

## Import der Vorlage
Um diese Vorlage in Overleaf zu importieren gibt es zwei Möglichkeiten.
1. Download dieser Vorlage über den grünen Button "Code" und dannn als "Download ZIP". Als nächstes kann in Overleaf unter "Neues Projekt" ein eine Vorlage als ZIP-Datei hochgeladen werden.
2. Verbindet euren Overleaf Account mit GitHub. Geht dazu in die Einstellungen von Overleaf. Danach müsst ihr auf GitHub dieses Projekt mit eurem eigenen GitHub-Account "Forken". Dazu geht ihr auf GitHub auf den Button "Fork" und dann "Create Fork". Damit erstellt ihr eure eigene Kopie dieses Projekts. In Overleaf könnt ihr nun das Projekt aus GitHub importieren. Der Vorteil dieser Methode ist, dass ihr eigene Änderungen, wie zum Beispiel die Daten auf dem Deckblatt, in euer eigenes Projekt pushen könnt. Nun habt ihr immer eure persönliche Vorlage mit euren Daten parat. Sollte ich weitere Änderungen an diesem Projekt vornehmen, könnt ihr diese einfach "pullen" um sie in eure Kopie des Projekts zu übernehmen.  

## Verwendung
1. In die main.tex wird kein Inhalt geschrieben. Hier werden bei Bedarf benötigte Pakete hinzugefügt oder weitere Kapitel(Aufgaben) importiert.
2. Füllt die Datei Deckblatt.tex im Ordner chapters mit euren Daten aus.
3. Schreibt eure Vorbereitung in den Versuch unter chapters/Vorbereitung.tex. Im Inhaltsverzeichnis erhält die Versuchsvorbereitung keine Kapitelnummer um die von der Fakultät gegebenen Protokollanforderungen zu erfüllen.
4. Laut Vorgabe der Fakultät soll das erste Kapitel die theoretischen Grundlagen des Versuchs erklären. Dies fällt häufig mit der versuchsvorbereitung zusammen. Die Versuchsvorbereitung kann in diesem Fall entfernt werden.
5. Das zweite Kapite beinhaltet den experimentellen Versuchsaufbau, das dritte die Durchführung und das vierte kapitel beinhaltet die Auswertung samt Fehlerrechnung. 
6. Anhänge wie Grafiken oder das Messprotokoll werden im Ordner include abgelegt. Es macht Sinn für jedes Kapitel einen Unterordner in include anzulegen um Ordnung zu bewahren. Somit könnt ihr die Grafiken schneller wieder finden, wenn sie ausgetauscht werden müssen.
7. Tauscht die Dateien Aufgabenblatt.pdf und Messptrotokoll.pdf durch das entsprechende Aufgabenblatt und euer eingescanntes, unterschriebenes Messprotokoll aus.

## Copy-Paste Vorlagen
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Grafiken einfügen

\begin{figure}[h] % h for here; t for top; b for bottom; ! overrides internal parameters LaTeX uses for determining "good" float positions
\centering Zentrieren der Grafik auf der Seite
\includegraphics[scale=0.3]{include/}
\caption{} % Grafiken haben Untertitel
\label{} % Label zum refenzieren mit \ref{}
\end{figure}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Tabellen einfügen

\begin{table}[!htb] % h for here; t for top; b for bottom; ! overrides internal parameters LaTeX uses for determining "good" float positions
    \centering % Zentrieren der Tabelle auf der Seite
    \caption{} % Tabellen haben Überschriften!
    \label{} % Label zum refenzieren mit \ref{}
    \begin{tabular}{c|c|c} % c steht für centering des Inhalts in der Spalte, mit | können weitere Spalten hinzugefügt werden
\toprule
Text & Text & Text\\
\midrule
Text & Text & Text\\
\hline
Text & Text & Text\\
\hline
Text & Text & Text\\
\bottomrule
    \end{tabular}
\end{table}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Gleichungen

\begin{equation} % equation Umgebung wird für einzeilige Gleichungen verwendet
  a^2 + b^2 = c^2
  \laben{} % Label zum refenzieren mit \ref{}
\end{equation}

% align Umgebung wird für mehrzeilige Gleichungen verwendet. Die Gleichungen werden am Gleichheitszeichen (&=) ausgerichtet  
\begin{align}
  a^2 + b^2 &= c^2\\
  c^2 &= a^2 + b^2
  \label{} % Label zum refenzieren mit \ref{}
\end{align}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Wertangaben

Entweder:
\begin{equation}
  \mathrm{Name} = \SI{Wert}{Einheit}
\end{equation}

oder
\begin{equation}
  \mathrm{Name} = Wert\,\mathrm{Einheit}
\end{equation}

Fehler-Rechnung Wertangabe

\begin{align}
  \mathrm{Name} = Wert \pm Wert \mathrm{(\delta_{stat})} \pm Wert \mathrm{(\delta_{sys})}\mathrm{Einheit}
\end{align}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Fußnote

% kann im Text eingebaut werden. Eine Fußnote erscheint im Text. Der Inhalt erscheint im Footer der Seite
\footnote{Quelle}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Listen erstellen

\begin{itemize}
\item Listenpunkt 1
\item Listenpunkt 2
\end{itemize}
