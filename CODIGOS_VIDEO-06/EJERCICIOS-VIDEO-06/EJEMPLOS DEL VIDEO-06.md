PRACTICA  CON ESTOS EJEMPLOS DEL VIDEO-06

  Exercises
Use the following exercises to improve your knowledge 

Exercise 1: Explore TF-IDF similarity.
Objective : Run the baseline TF-IDF demo, and observe cosine-similarity patterns.
Tasks:
1 Open document_vector_similarity.py from the listings folder.
2 Save a copy as exercise1_tfidf_demo.py.
3 Run the script, enter “blue” when prompted, and choose three matches.
4 Note which three sentences appear, and record their similarity scores.
5 Repeat with the query “breakfast,” and capture the new results.
Expected duration: 8 minutes

Exercise 2: Swap in OpenAI embeddings.
Objective : Convert the similarity demo to use semantic embeddings instead of TF-IDF.
Tasks:
1 Duplicate the previous file as exercise2_embeddings_demo.py.
2 Replace the TfidfVectorizer block with the get_embedding helper from listing 6.4.
3 Remove the plotting section, and print the raw cosine-similarity matrix.
4 Run the script twice (queries “blue” and “breakfast”), and compare rankings to exercise 1.
5 Add a brief comment at the end explaining one sentence that moved up or down and why.
Expected duration: 12 minutes

Exercise 3: Persist vectors in Chroma DB.
Objective : Store embeddings in a local Chroma DB collection, and perform similarity search.
Tasks:
1 Copy document_query_chromadb.py to exercise3_chroma_store.py.
2 Change the collection name to exercise_docs, and ensure collection.add() is called only if it is empty.
3 Run the script. At the prompt enter “lazy dog,” and request three matches.
4 Verify that IDs, distances (< 0.5), and texts print correctly.
 

5 Restart the script to confirm the collection loads from disk without re-adding vectors.
Expected duration: 10 minutes

Exercise 4: Build a vector-only RAG agent.
Objective : Create an agent that answers “Back to the Future” questions using vector search only.
Tasks:
1 Open 02_RAG_agent_vector.py, and save as exercise4_vector_rag_agent.py.
2 Change max_tokens in simple_chunk to 150 to create smaller chunks. Rerun the embedding step if needed.
3	Ask the agent “Who is Pine City’s mayor in the script?” and copy the answer.
4 Ask “What happens at 10:04 PM?” and observe whether the agent can find the scene.
5  In a comment, explain one limitation you notice with vector-only retrieval.
Expected duration: 14 minutes

Exercise 5: Implement and trace a hybrid RAG agent.
Objective : Combine keyword and vector tools, enforce grounding, and inspect the deci-sion path.
Tasks:
1 Duplicate 02_RAG_agent_hybrid.py to exercise5_hybrid_rag_agent.py.
2 Inside the prompt, add a requirement to cite at least two distinct references for every answer.
3  Wrap the main Runner.run_sync call with trace("Chapter 6 Hybrid RAG Demo"):...
4 Pose the query “At what exact time does the lightning strike the clock tower?” and record the output.
5 Open OpenAI > Dashboard > Traces, and confirm you see both search_script_ with_keyword and search_script_with_vector_similarity calls followed by the grounded answer.
Expected duration: 15 minutes
