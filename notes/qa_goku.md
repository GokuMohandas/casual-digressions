## - [A Gentle Analysis of Recent Deep Q/A Architectures]

Make  a TLDR
Insert Gif of the DCN UI

TBALE ON CONTENTS


Introduction to Deep Q/A architecture, mainly focused on the recent developments by Salesforce team (DMN/DMN+ from Metamind) and University of Washington/ Allen Institute for Artificial Intelligence (BiDAF). 

Mention that you will do a deep dive analysis for the DMN+ model just to show what the pipeline looks like and will release deep dives with implementation for DCN and BiDAF as well.

What dose Q/A look like (babI examples, SQuAD examples, etc.)? What can we do, what can't we do? Link to Socher's talk.

Analysis/Implementations:
DMN+ 
	   Briefly mention DMN and link to tutorial), big diff is not using supporting facts
	   Provide short summary of DMN+ and link to tutorial
	   Show architecture from paper with citations
	   Show some preprocessing images.
	   Provide shapes breakdown with plots (don't forget episode plot from DMN paper)
	   Talk about why you used gradient noise (Neelakantan paper) and provide citation
	   Provide code for certain parts of the shapes breakdown (for better understanding for readers)   
DCN
	Summarize main idea
	Provide architecture diagrams with citations
	Talk about cool aspects of architecture but also down falls
BiDAF
	Summarize main idea, mention it is currently 2nd
	Provide architecture diagrams with citations
	Talk about cool aspects of architecture but also down falls
	
Model Interpretation:
	Show what the model sees and some of the Q/A images (for DMN+ and DCN).

SQuAD leaderboard (talk about very competitive and collaborative community). SOTA lasting for more than 2 weeks is starting to become rare.

What is left to do? What are the next steps? Talk about joint networks and similar work being done with knowledge bases and logical reasoning, etc. Point to work by Salesforce and Pete SCOMAROCKS STARTUP  AND also mention MSFT (currently leading on SQUAD) but talk about "we are more than likely to see that fluctuate very soon). 

GitHub Repo: Implementations will be uploaded soon (BiDAF is still WIP), along with UI for all models to test out your own inputs. Follow on
Twitter for updates! [FOLLOW BUTTON]

Citations!!! (4 articles and maybe a few more from back of DMN+ paper and gradient noise paper_



- 



