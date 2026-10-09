# Task 1 

Name: Fares Elamin
ID: 58-0536

## Explanation

The raw file had 39 rows. Looking at value_counts() showed that faculty, club and city were written in many ways such as: 

pharma, Media Engineering and Technology, Chess Club, Soccer, Alex, El Giza

So I stripped spaces and lower-cased them and mapped every remaining variant to its canonical value and asserted that only the allowed values remain. Some names had extra spaces and mixed capitals so I collapsed repeated spaces and trimmed them and used Title Case.Emails were trimmed and lower-cased. 

fee_paid had nine text forms (Y, yes, TRUE, 1, no, 0 ), which I mapped to a real boolean column. 

signed_up_at mixed YYYY-MM-DD HH:MM (25 rows) and DD/MM/YYYY HH:MM (14 rows); I read the slash format as day first because its first number reaches 18, and parsed each format separately into one datetime column. 

Removing 3 exact duplicates (S015, S022, S023) left 36 rows; removing 4 repeated sign-ups for the same student_id and club left 32. I kept the latest submission because in every pair the earlier row had fee_paid False and the later one True, so the latest is the current truth. 

Order matters as deduplicating before fixing club spellings finds only 2 repeats instead of 4 and since Music/music and Debate/debate club look different which leaves 34 rows. Two different students are both named Mohamed Adel, but I deduplicated on student_id   (61-4844 and 55-2992) and never on name or email, so they stay separate.