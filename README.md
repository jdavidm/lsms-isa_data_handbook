# LSMS-ISA Handbook on Data Processing
## Processed Dataset Construction and Documentation

The data handbook is an annotated code book listing and explaining the procedures used to clean and prepare a household agricultural production dataset from the the Nigeria General Household Survey, Panel 2012-2013, Wave 2. The agricultural production dataset is designed to estimate crop production functions at the household level. There are 6 preliminary guide documents on the making of datasets for fertilizer, harvest labor, planting labor, crop output, pesticide-herbicide-fungicide-irrigation, and land area. There is a final guide called "yield" which combines the preliminary datasets to make a dataset ready to estimate crop production functions.

The basic steps we take here are the same steps you could take to generate yield variables in other waves and for other crops in the Nigeria General Household Survey. The steps are also applicable to other surveys in the Living Standards Measurement Study - Integrated Surveys on Agriculture (LSMS-ISA) program from the World Bank. 

The guide combines the code, the explanations of the code, and the output in a single document. The user generates the guide by running a stata do file that runs the code with the data and compiles the results into a single document. To compile the guide please follow the steps below.

This work made possible through funding from the World Bank and from the Berkeley Initiative for Transparency in the Social Sciences (BITSS), managed by the Center for Effective Global Action (CEGA). 

***Instructions for Mac OS users are below the instructions for Microsoft Windows***

## For Microsoft Windows:

##  Getting Started: Setting Up A Dev Environment  

Before we compile the documents we must clone the git repository on our local computer and set up the file structure that will contain the raw data.

### Steps:
1. We use pandoc to compile the guide word document. Pandoc can be downloaded from https://pandoc.org/installing.html. Install pandoc with this path when prompted in the pandoc installation guide where to save pandoc: "C:/Users/USERNAME/AppData/Local/Pandoc/pandoc.exe". If pandoc was already installed or installed with another path then copy your local path for `pandoc.exe` and continue following this guide, when you reach step 4 you will be directed to paste that path into a do file. 

2. Download a local copy of the code (clone the repository)
   
  Open Github desktop. From the `file` menu in the uppermost tool bar select `clone repository...`. In the `clone repository` menu select the `URL` tab and and in the first box paste the following URL:
  
   ```sh 
  https://github.com/jdavidm/lsms-isa_data_handbook 
   ```
  Or alternatively paste the following username/repository_name:
   
   ```sh 
   jdavidm/lsms-isa_data_handbook
   ```
 
   After the github has located the repository select the `clone repository` button.
   
  Once the repository has been cloned to your local, locate the "lsms-isa_data_handbook" file in the local "git" folder and open the ***"project.do"*** in stata.
   
3. Edit the "project.do"
 
   The "project.do" creates a local file directory to store the raw datasets and the cleaned dataset and the "project.do" runs the code compile the guide. We have to do a bit of global path editing on "project.do" to work for your unique local computer username. The edits are specific to your computer and will allow the "project.do" file to use and create the paths on and for your local computer.
   
  In the do file editor open project.do. On the project.do on line 30, 31, and 34 replace "USERNAME" with your unique local computer username.
   
   ```
       if `"`c(username)'"' == "USERNAME" {	
        global 		project  	"C:/Users/USERNAME/git/lsms-isa_data_handbook"	
		
		* tell Stata where to find the relevant programs
		whereis pandoc 			"C:/Users/USERNAME/AppData/Local/Pandoc/pandoc.exe"
    }
   ```
   **If pandoc.exe was installed with a different path then now is the time to replace "C:/Users/USERNAME/AppData/Local/Pandoc/pandoc.exe" on line 34 with pandoc.exe's path in your local computer.**
   
   The rest of "project.do" is divided into sections: the directory creation section, `global 			dirCreate	0`,
the stata package installation section, `global 			pack 		0`, and the building the handbook section, `global			document	0`. Each of these sections can be turned "on" by changing the 0 to 1 or turned "off" by turning the 1 to a 0. A section will only run when it is turned "on". By default `dirCreate` and `pack` secions are "on"; the `document` section is off, only turn it on once you have completed step four.
 
4. Download the General Household Survey, Panel 2012-2013, Wave 2 for Nigeria, 2012-2013 at https://microdata.worldbank.org/index.php/catalog/1952/get-microdata. You will need to create an account with the World Bank if you do not already have one. You will be asked to provide a reason for downloading the data.
 
   The dataset file is called NGA_2012_GHSP-W2_v02_M_STATA. ***Extract the entire file NGA_2012_GHSP-W2_v02_M_STATA and copy or move it to*** `C:\Users\"username"\git\lsms-isa_data_handbook\data\nigeria\wave_2\raw` - the folders in this path were created by the project.do.

 5. Generating the handbook.

    Open the "project.do" and in the `setup` section turn on the `document` section.
 
 ## Compiling the Guide in Microsoft Word:
 
1.  Run the "project.do" file to generate all chapters of the guide in Microsoft Word documents. 

2. Save each chapter of the guide in Microsoft Word individually. You now have the cleaned data and the guide.
   
 ## For Mac OS:
 
 ##  Setting Up a Dev Environment:
 
Before we compile the documents we must clone the git repository on our local computer and set up the file structure that will contain the raw data.

### Steps:
1. We use pandoc to compile the guide word document. Pandoc can be downloaded from https://pandoc.org/installing.html. Install pandoc with this path when prompted in the pandoc installation guide where to save pandoc: /usr/local/bin/pandoc. If pandoc was already installed or installed with another path then copy your local path for `pandoc.exe` and continue following this guide, when you reach step 4 you will be directed to paste that path into a do file. 

2. Download a local copy of the code (clone the repository)
   
  Open Github desktop. From the `file` menu in the uppermost tool bar select `clone repository...`. In the `clone repository` menu select the `URL` tab and and in the first box paste the following URL:
  
   ```sh 
  https://github.com/jdavidm/lsms-isa_data_handbook 
   ```
  Or alternatively paste the following username/repository_name:
   
   ```sh 
   jdavidm/lsms-isa_data_handbook
   ```
 
   After the github has located the repository select the `clone repository` button.
   
  Once the repository has been cloned to your local, locate the "lsms-isa_data_handbook" file in the local "git" folder and open the ***"project.do"*** in stata.
   
3. Edit the "project.do"
 
   The "project.do" creates a local file directory to store the raw datasets and the cleaned dataset and the "project.do" runs the code compile the guide. We have to do a bit of global path editing on "project.do" to work for your unique local computer username. The edits are specific to your computer and will allow the "project.do" file to use and create the paths on and for your local computer.
   
  In the do file editor open project.do. On the project.do on line 30, 31, and 34 replace "USERNAME" with your unique local computer username.
  
   ```
       if `"`c(username)'"' == "USERNAME" {	
        global 		project  	"/Users/USERNAME/git/lsms-isa_data_handbook"	
		
		* tell Stata where to find the relevant programs
		whereis pandoc 			/usr/local/bin/pandoc
    }
   ```
   **If pandoc was installed with a different path then now is the time to replace /usr/local/bin/pandoc on line 34 with pandoc's path in your local computer.**
   
   The rest of "project.do" is divided into sections: the directory creation section, `global 			dirCreate	0`,
the stata package installation section, `global 			pack 		0`, and the building the handbook section, `global			document	0`. Each of these sections can be turned "on" by changing the 0 to 1 or turned "off" by turning the 1 to a 0. A section will only run when it is turned "on". By default `dirCreate` and `pack` secions are "on"; the `document` section is off, only turn it on once you have completed step four.

4. Download the General Household Survey, Panel 2012-2013, Wave 2 for Nigeria, 2012-2013 at https://microdata.worldbank.org/index.php/catalog/1952/get-microdata. You will need to create an account with the World Bank if you do not already have one. You will be asked to provide a reason for downloading the data.
 
   The dataset file is called NGA_2012_GHSP-W2_v02_M_STATA. ***Extract the entire file NGA_2012_GHSP-W2_v02_M_STATA and copy or move it to*** `\Users\"USERNAME"\git\lsms-isa_data_handbook\data\nigeria\wave_2\raw` - the folders in this path were created by the project.do.
 
 5. Generating the handbook.

    Open the "project.do" and in the `setup` section turn on the `document` section.
 
## Compiling the Guide in Microsoft Word:

1. Run the "project.do" file to generate all chapters of the guide in Microsoft Word documents.

2. Save each chapter of the guide in Microsoft Word individually. You now have the cleaned data and the guide.
   
  
