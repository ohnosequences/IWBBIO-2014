---
title: 'Statika: managing cloud resources, bioinformatics tools and data'
author: 
    - Alexey Alekhin,
    - Evdokim Kovach,
    - Pablo Pareja-Tobes,
    - Marina Manrique,
    - Eduardo Pareja,
    - Raquel Tobes,
    - Eduardo Pareja-Tobes
date: 07.04.2014
institute: 'Era7 Bioinformatics'
---

\begin{columns}[t] 
% The whole poster consists of three major columns, the second of which is split into two columns twice - the [t] option aligns each column's content to the top

\begin{column}{\sepwid}\end{column}

\begin{column}{\onecolwid}

%----------------------------------------------------------------------------------------
%   OBJECTIVES
%----------------------------------------------------------------------------------------

\begin{alertblock}{Introduction}

Statika is a set of Scala libraries which % allows you to declare dependencies between components of any modular system and deploy them.

\begin{itemize}
\item allows building \textit{well-structured} module systems
\item where dependencies are \textit{correct by construction}
\item and you know it \textit{before you run} anything
\end{itemize}

\end{alertblock}

\vspace{1cm}

\begin{block}{Basic notions}

\begin{center}\textbf{Bundle}\end{center}

A \textbf{bundle} is a thin wrapper for a tool, library, resource or any other component of your system:

\begin{itemize}
\item It may have dependencies on other bundles.
\item It may do something in runtime, e.g. install a tool, that it represents.
\end{itemize}


\begin{center}\textbf{Distribution}\end{center}

A \textbf{distribution} is a bundle, which can deploy other bundles (it's members):

\begin{itemize}
\item It represents some environment, where you're going to use your bundles.
\item Being a member of a distribution means to work fine with this environment.
\item Distribution takes care of installing member dependencies first, and then the member itself.
\end{itemize}

\end{block}

\vspace{1cm}

\begin{alertblock}{Availability}

\begin{center}
\begin{tabular}{m{0.5\linewidth} m{0.48\linewidth}}
\includegraphics[width=\linewidth]{resources/logos/agplv3-logo.png} \newline Statika is free and open-source under the \mbox{AGPLv3} license & \includegraphics[width=\linewidth]{resources/images/qrcode.png} 
\end{tabular}

See \href{http://ohnosequences.com/statika}{http://ohnosequences.com/statika}
\end{center}

\end{alertblock}



\end{column}


\begin{column}{\sepwid}\end{column}
\begin{column}{\onecolwid}


\begin{block}{Abstract module system}

\begin{itemize}
\item Bundles are represented as Scala types.
\item Their dependencies on each other are validated by compiler --- i.e. \textbf{statically}.
\item Statika linearizes the types graph to get them in the right order.
\end{itemize}

\end{block}

\begin{center}
\includegraphics[width=\linewidth]{resources/images/StatikaLinearization.png}
\end{center}

\vspace{2cm}

\begin{block}{Artifacts management}

\textbf{sbt-statika} --- an sbt (simple build tool) plugin, which takes care of

\begin{itemize}
\item packing bundles into versioned artifacts (jars)
\item reusing sbt infrastructure to track dependencies on the artifact level
\item standardizing common settings, versioning and release process
\end{itemize}

\end{block}

\vspace{1.5cm}

\begin{block}{Deployment}

Amazon Web Services + \textbf{aws-statika} library

\begin{itemize}
\item Bundles can be \textit{applied}, i.e. deployed to an EC2 instance
\item Statika \textit{distributions} abstract over the cloud infrastructure specifics
\end{itemize}

\end{block}


\end{column}




\begin{column}{\sepwid}\end{column}
\begin{column}{\onecolwid}


\begin{block}{Applications in bioinformatics}

\vspace{1cm}
\begin{center}
\begin{tabular}[c]{m{0.3\linewidth}cc}
\includegraphics[width=\linewidth]{resources/logos/bio4j-logo.png} & \hspace{0.5cm} & \Large{\textbf{Graph Database}}
\end{tabular}
\end{center}
\vspace{1cm}

Bio4j is a bioinformatics graph database which integrates data from a lot of different sources:

\includegraphics[width=\linewidth]{resources/images/Bio4jModules.png}

% \vspace{1.5cm}

Every module has some inner structure:

\begin{itemize}
\item raw data from a data source
\item data importing process to the graph database
\item nodes and relationships type definitions
\item some abstract interface representing what you can do with this data
\end{itemize}

\includegraphics[width=\linewidth]{resources/images/Bio4jModulesExampleIncremental.png}

So Statika introduces to Bio4j a flexible module system with

\begin{itemize}
\item simple data-import process
\item automized dependencies management
\item easy and robust deployment to AWS
\end{itemize}

\end{block}


\end{column}

\begin{column}{\sepwid}\end{column}
\begin{column}{\onecolwid}

\begin{block}{Applications in bioinformatics}

\vspace{1cm}
\begin{center}
\includegraphics[width=0.5\linewidth]{resources/logos/nispero-logo.png}\\
\large{\textbf{Cloud-computing System}}
\end{center}
% \vspace{1cm}

Nispero is a toolset for declaring scalable cloud-based systems for bioinformatics computations. It has pretty complex inner commponents structure, which is managed with the help of Statika:

\begin{center}
\includegraphics[width=0.9\linewidth]{resources/images/NisperoBundles.png}\\
\vspace{1cm}
\rule{0.9\linewidth}{.1pt}
\vspace{1cm}
\end{center}


There is also a Statika distribution for bioinformatics tools, such as Velvet, Cufflinks, Tophat and Bowtie(2). See github.com/statika/bioinfo-dist/.

\end{block}


\begin{alertblock}{Acknowledgments}

Statika is developed by the R\&D team of the Era7 Bioinformatics company\\

\vspace{1cm}
\begin{center}
\includegraphics[width=0.7\linewidth]{resources/logos/era7-logo.png}\\
\vspace{1cm}
\includegraphics[width=0.7\linewidth]{resources/logos/ohnoseq-logo.png}\\
% \vspace{1cm}
\end{center}

This project is funded in part by the ITN FP7 project INTERCROSSING (Grant 289974)\\

\begin{center}
\begin{tabular}{m{0.4\linewidth} m{0.4\linewidth}}
\includegraphics[width=\linewidth]{resources/logos/intercrossing-logo.png} & \includegraphics[width=\linewidth]{resources/logos/marie-curie-logo.png}
\end{tabular}
\end{center}

\end{alertblock}

\end{column}

\end{columns}
