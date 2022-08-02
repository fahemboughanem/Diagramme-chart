# Diagramme-chart
Diagramme
\documentclass{article}

\usepackage{tikz}
\usetikzlibrary{shapes.geometric,arrows.meta}
\usetikzlibrary{positioning}
\usetikzlibrary{calc}

\begin{document}

\tikzstyle{diam} = [diamond, aspect=2, draw, fill=red!40, text width=6em,text centered ]
\tikzstyle{block} = [rectangle, draw, fill=blue!20, text width=3cm,text centered, rounded corners, minimum height=2em ]
\tikzstyle{trap} = [trapezium, trapezium left angle=70, trapezium right angle=110, minimum height=2em, text centered, draw=red, fill=green!30]
\tikzstyle{rect} = [rectangle, minimum width=3cm, minimum height=1cm, text centered, draw=red, fill=orange!30]
\tikzstyle{line} = [draw, -latex]

\begin{tikzpicture}[node distance=1cm and 1cm]

    % place nodes
    \node [rect] (init) {start here} ;
    \node [diam, below=of init] (decision-1) {decision?} ;
    \node [block, right=of decision-1, yshift=1cm] (block-1) {block-1} ;
    \node [block, below=of decision-1, yshift=-1cm] (block-2) {block-2} ;
    \node [block, right=of block-2] (block-3) {block-3 very long text, I am adding more text} ;
    \node [diam, below=of block-3] (decision-2) {decision-2?} ;
    \node [block, right=of decision-2] (block-4) {block-4} ;
    \node [diam, below=of decision-2] (decision-3) {decision-3?} ;
    \node [block, left=of decision-3] (block-6) {block-6} ;
    \node [block, right=of decision-3] (block-5) {block-5} ;
    \node [block, below=of block-6] (block-7) {block-7} ;
    \node [block, right=of block-7] (block-8) {block-8} ;
    \node [trap, right=of block-8] (block-9) {block-9} ;

    % draw edges
    \path [line] (init) -- (decision-1) ;
    \path [line] (decision-1) -| node[right] {yes} (block-1) ;
    \path [line] (decision-1) -- node[left] {no}(block-2) ;
    \path [line] (block-2) -- (block-3) ;
    \path [line] (block-3) -- (decision-2) ;
    \draw [line] (block-4) -- (block-3);
    \draw [line] (block-4) |- (block-3);
    \path [line] (decision-2) -- node[above] {no} (block-4) ;
    \path [line] (decision-2) -- node[fill=white] {yes} (decision-3) ;
    \path [line] (decision-3) -- node[above] {yes} (block-6) ;
    \path [line] (decision-3) -- node[below] {no} (block-5) ;
    \path [line] (block-6) -- (block-7) ;
    \path [line] (block-7) -- (block-8) ;
    \path [line] (block-8) -- (block-9) ;

    \path[<->] (block-7.west) edge[bend left=50] (block-2.west) ;
    \path[line, rounded corners] (init.west) -| ($(init.west) - (1,1)$) |- (block-2.west) ;

\end{tikzpicture}

\end{document}
