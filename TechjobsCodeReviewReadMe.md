**************************************************************
Assignment1 TechJobs
LaunchCode Homework
**************************************************************
Task 1
Print Jobs
**************************************************************
Below is found in TechJobs.cs
**************************************************************
public void PrintJobs(List<Dictionary<string, string>> someJobs)
        {
            if (someJobs.Count == 0)
            {
                Console.WriteLine("No results");
            }

            foreach (Dictionary<string, string> job in someJobs)
            {

                Console.WriteLine($"{Environment.NewLine}*****");
                foreach (KeyValuePair<string, string> kvp in job)
                {
                    Console.WriteLine($"{kvp.Key}: {kvp.Value}");

                }
                Console.WriteLine("*****");

            }
        }
 **************************************************************
Section below explains function above
 **************************************************************       
This C# function called PrintJobs that takes a List of Dictionaries as an input parameter. Each Dictionary in the List represents a job, where the keys represent job attributes such as "title", "description", and "location", and the values represent the corresponding attribute values.

The function first checks if the input List is empty by checking the count of the List. If the count is 0, it prints "No results" to the console.

If the input List is not empty, the function uses a foreach loop to iterate over each Dictionary (job) in the List. For each job, it first prints "" on a new line using the Console.WriteLine method, along with a Environment.NewLine constant to ensure the "" is printed on a new line.

It then uses another foreach loop to iterate over each key-value pair in the Dictionary, and prints the key and value separated by a colon and space using the Console.WriteLine method. This prints each job attribute and its corresponding value to the console.

After printing all the key-value pairs for the current job, the function prints "*****" again on a new line using Console.WriteLine.

Overall, this function is designed to print a list of jobs to the console in a specific format that separates each job with asterisks and prints each job's attributes and values.
**************************************************************



**************************************************************
Task 2
FindByValue
**************************************************************
Below is found in JobData.cs line 45
**************************************************************
public static List<Dictionary<string, string>> FindByValue(string value)
        {
            //.Contains(value);
            // load data, if not already loaded
            LoadData();
            List<Dictionary<string, string>> newList = new List<Dictionary<string, string>>();
            foreach (Dictionary<string, string> job in AllJobs)
            {
                foreach (string thing in job.Keys)
                {
                    if (job[thing].ToLower().Contains(value.ToLower()))
                    {
                        newList.Add(job);
                    }
                }
            }
**************************************************************
Section below explains function above
**************************************************************            
This is a C# function called FindByValue that takes a string value as an input parameter. The purpose of the function is to search for all jobs that contain the given value in any of their attributes, and return a list of those jobs in the form of a List<Dictionary<string, string>>.

The function first calls another function called LoadData() to ensure that the job data has been loaded into the program.

It then initializes a new empty List of Dictionary objects called newList that will be used to store the matching jobs.

The function then loops through each job dictionary in the AllJobs list (presumably a static list of all jobs available in the program). For each job dictionary, it loops through each attribute (key) in the dictionary.

For each attribute, the function checks if the attribute's value (the string associated with the key) contains the given value string in a case-insensitive manner. If it does, the function adds the entire job dictionary to the newList.

Finally, the function returns the newList containing all the job dictionaries that contain the given value in any of their attributes.

Overall, this function is designed to search for jobs in a list of dictionaries based on a given value and return a list of all the job dictionaries that contain that value in any of their attributes.
**************************************************************
Below is found in TechJobs.cs line 66
**************************************************************
  if (columnChoice.Equals("all"))
                    {
                        List<Dictionary<string, string>> searchResults =
                       JobData.FindByValue(searchTerm);
                        PrintJobs(searchResults);
                    }

**************************************************************
Section below explains function above
**************************************************************
This is a code block that executes when the user chooses to search for the input searchTerm across all columns of the job data.

The code block checks if the value of the columnChoice variable is equal to the string "all", indicating that the user wants to search across all columns.

If the columnChoice is equal to "all", the FindByValue method of the JobData class is called with the searchTerm as the argument to find all job dictionaries that contain the input searchTerm in any of their values. The resulting list of job dictionaries is stored in the searchResults variable.

Finally, the PrintJobs method is called with the searchResults list as the argument to print out all the matching job dictionaries to the console.
**************************************************************


**************************************************************
Task 3
Make Search Methods Case-Insensitive
**************************************************************
Considerations
**************************************************************
Which methods are called when searching?
How is the user’s search string compared against the values of fields of the job Dictionary objects?
How can you make this comparison in a way that effectively ignores the case of the strings?
How can you do this without altering the capitalization of the items in AllJobs so that the data gets printed out the same way that it appears in job_data.csv?
**************************************************************
PrintJobs function is not involved in the searching process. It is a function that is called to print the jobs that are found by FindByValue function.

FindByValue function is the method called when searching. It loads the data if not already loaded and searches through the loaded jobs data to find the jobs that contain the given value.

To compare the user's search string against the values of fields of the job Dictionary objects in a way that ignores the case of the strings, the function calls the ToLower() method on both the search string and the job attribute value before comparing them using the Contains() method. This converts both strings to lowercase and ensures that the comparison is case-insensitive.

The capitalization of the items in AllJobs is not altered in the searching process. The ToLower() method is only called when comparing the search string and the job attribute value. The original capitalization of the items in AllJobs remains the same, so the data gets printed out the same way that it appears in the job_data.csv file.
**************************************************************




**************************************************************
Additional Function considerations
**************************************************************
Below is found in Jobdata.cs
**************************************************************
  //TODO: Complete the FindByValue method
        public static List<Dictionary<string, string>> FindByValue(string value)
        {
            //.Contains(value);
            // load data, if not already loaded
            LoadData();
            List<Dictionary<string, string>> newList = new List<Dictionary<string, string>>();
            foreach (Dictionary<string, string> job in AllJobs)
            {
                foreach (string thing in job.Keys)
                {
                    if (job[thing].ToLower().Contains(value.ToLower()))
                    {
                        newList.Add(job);
                    }
                }
            }


            return newList;
        }"
**************************************************************
Section below explains function above
**************************************************************
This C# method called FindByValue that takes a string value as input and returns a list of dictionaries containing job information that matches the input value.

The LoadData() method is called at the beginning of the function to ensure that the data is loaded before searching.

A new empty list of dictionaries called newList is created to store the job dictionaries that match the input value.

The method then loops through all the job dictionaries in the AllJobs list. For each job dictionary, it loops through all the keys of the dictionary to find any key-value pairs that match the input value.

The ToLower() method is used to convert both the input value and the dictionary values to lowercase before checking if the dictionary value contains the input value using the Contains() method. This ensures that the search is case-insensitive.

If a matching key-value pair is found, the job dictionary is added to the newList list.

Finally, the function returns the newList list containing all the job dictionaries that match the input value.

The function is incomplete as indicated by the //TODO comment, and there might be additional functionality or modifications that need to be added to it to complete the intended functionality.
**************************************************************
Below is found in Jobdata.cs line 45
**************************************************************
            LoadData();

            List<Dictionary<string, string>> jobs = new List<Dictionary<string, string>>();

            foreach (Dictionary<string, string> row in AllJobs)
            {
                string aValue = row[column];


                //TODO: Make search case-insensitive
                if (aValue.ToLower().Contains(value.ToLower()))
                {
                    jobs.Add(row);
                }
            }

            return jobs;
**************************************************************
This C# method that searches for a given value in a specific column of the job data loaded by the LoadData() method.

At the beginning of the method, the LoadData() method is called to ensure that the data is loaded before searching.

A new empty list of dictionaries called jobs is created to store the job dictionaries that match the input value.

The method then loops through all the job dictionaries in the AllJobs list. For each job dictionary, it extracts the value associated with the specified column and stores it in the aValue variable.

The method then checks if the aValue variable contains the given value by calling the ToLower() method on both strings to make the search case-insensitive. If a matching value is found, the job dictionary is added to the jobs list.

Finally, the function returns the jobs list containing all the job dictionaries that match the input value in the specified column.
**************************************************************
Below is found in TechJobs.cs line 40
**************************************************************
					if (columnChoice.Equals("all"))
                    {
                        List<Dictionary<string, string>> searchResults =
                       JobData.FindByValue(searchTerm);
                        PrintJobs(searchResults);
                    }"
**************************************************************
Section below explains code block above
**************************************************************
This is a code block that executes when the user chooses to search for the input searchTerm across all columns of the job data.

The code block checks if the value of the columnChoice variable is equal to the string "all", indicating that the user wants to search across all columns.

If the columnChoice is equal to "all", the FindByValue method of the JobData class is called with the searchTerm as the argument to find all job dictionaries that contain the input searchTerm in any of their values. The resulting list of job dictionaries is stored in the searchResults variable.

Finally, the PrintJobs method is called with the searchResults list as the argument to print out all the matching job dictionaries to the console.                    

