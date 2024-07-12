\documentclass{article}
\usepackage{listings} % For code listings

\begin{document}

\title{Creating a Kubernetes Pod with YAML File}
\author{}
\date{}
\maketitle

\section{Introduction}

This guide outlines the steps to create a Kubernetes Pod using a YAML file (\texttt{pod.definition.yml}) and \texttt{kubectl}.

\section{Prerequisites}

Before you begin, ensure you have the following:
\begin{itemize}
  \item Kubernetes cluster running (e.g., Minikube, Docker Desktop with Kubernetes enabled)
  \item \texttt{kubectl} command-line tool configured to communicate with your Kubernetes cluster
\end{itemize}

\section{Steps to Set Up and Create a Kubernetes Pod}

\subsection{Step 1: Create Directories}

Create necessary directories for your project and navigate into the \texttt{pod} directory.

\begin{lstlisting}[language=bash]
mkdir -p myproject/pod
cd myproject/pod
\end{lstlisting}

\subsection{Step 2: Write the Pod Definition YAML File}

Create a file named \texttt{pod.definition.yml} and add the following content. Replace \texttt{your-image} with the Docker image you want to use.

\begin{lstlisting}[language=yaml]
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
spec:
  containers:
    - name: your-image-container
      image: your-image
      # Add additional container configuration here if needed
\end{lstlisting}

\subsection{Step 3: Create the Pod}

\begin{lstlisting}[language=bash]
kubectl create -f pod.definition.yml
\end{lstlisting}

\begin{itemize}
  \item This command reads the YAML file (\texttt{pod.definition.yml}) and creates the Pod defined within it.
\end{itemize}

\subsection{Step 4: Verify Pod Creation}

\begin{lstlisting}[language=bash]
kubectl get pods
\end{lstlisting}

\subsection{Optional Step 5: Interact with the Pod}

\subsubsection{Get Pod Details}

\begin{lstlisting}[language=bash]
kubectl describe pod myapp-pod
\end{lstlisting}

\subsubsection{View Pod Logs}

\begin{lstlisting}[language=bash]
kubectl logs myapp-pod
\end{lstlisting}

\section{Additional Methods for Creating a Pod}

\subsection{Method 1: Using \texttt{kubectl run}}

You can create a Pod directly using the \texttt{kubectl run} command:

\begin{lstlisting}[language=bash]
kubectl run myapp-pod --image=your-image
\end{lstlisting}

\subsection{Method 2: Generate YAML Using \texttt{kubectl run} with \texttt{--dry-run}}

You can generate the YAML definition for a Pod using \texttt{kubectl run} with the \texttt{--dry-run} option:

\begin{lstlisting}[language=bash]
kubectl run myapp-pod --image=your-image --dry-run=client -o yaml > pod.generated.yml
\end{lstlisting}

\begin{itemize}
  \item This command performs a dry run to generate the YAML configuration for a Pod named \texttt{myapp-pod} using the image \texttt{your-image}. The YAML output is redirected (\texttt{>}) to a file named \texttt{pod.generated.yml}.
\end{itemize}

\subsection{Create the Pod Using Generated YAML}

After generating the YAML file, you can create the Pod using the generated configuration file:

\begin{lstlisting}[language=bash]
kubectl create -f pod.generated.yml
\end{lstlisting}

\end{document}




