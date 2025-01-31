# Gale-Shapley
Example implementation of Gale Shapley algorithm in Python.

## Algorithm:

- The number of applicants and companies, and each of their preferences lists are input.  
- All companies and applicants are marked as ‘free.’  
- Free companies accept applicants in order based on their preference lists.
-  If an applicant is unmatched, they will accept the offer from the company.  
- If the applicant is already matched, they will compare their current match to the new company. If they prefer the new company, they will switch to that company, and the previous company becomes free again.  
- The companies continue to accept applicants until all companies and all applicants are matched, and there are no blocking pairs.  
- The final list of the stable pairs is returned.

## Data Structures Used:

- **Dictionaries** - dictionaries were used to keep track of company preferences, applicant preferences, current matches, companies' choices in the next iteration, and applicant choices (which is a 2D dictionary used to efficiently check if an applicant prefers one company over another). Dictionaries were used for these things because of the quick access time.
  
- **Deque** - used to store free companies. The deque is used for efficient removal of the first company and addition of a company to the back after rejection.

## Time Complexity Analysis:

The overall time complexity of my implementation is **O(n^2)**. If we go through each part of the algorithm step by step, we see the time complexities for different steps are:

- **O(n)** to validate that the sizes of the preference lists are equal to `n`.
- **O(n^2)** to create `applicant_choices`, because we iterate over `n` applicants and create a dictionary for their preference list of companies.
- **O(n)** to create the `next_choice` dictionary, because an entry is created for each company.
- **O(n^2)** for the while loop. In the worst case, every single company will propose to every applicant before they receive a match.
- **O(n)** to create the list of pairs which is returned, because there are `n` pairs.

The worst time complexity out of all of these steps is **O(n^2)**, so we can say that the algorithm has a total time complexity of **O(n^2)**.
