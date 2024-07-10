# Replace space with '$'
```c
#include <stdio.h>
#include <string.h>


int main() {
    char str[100];
    scanf("%[^\n]s",str);
    
    int len = strlen(str) ,start =0;
    
    for(int i =0;i<=len;i++){
     if(str[i] == ' ')  printf("$");
     else printf("%c",str[i]);
    }

    return 0;
}

```
# Replace Space With '%20'
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%[^\n]s",str);
    char result[100];
    int result_index = 0;
    
    int len = strlen(str) ,start =0;
    
    for(int i =0;i<=len;i++){
        if(str[i] ==' '){
            result[result_index++] = '%';
            result[result_index++] ='2';
            result[result_index++] = '0';
        }else{
            result[result_index++] = str[i]; 
        }
    }
    result[result_index] = '\0';
    
    printf("%s\n",result);

    return 0;
}

```

# Max repeated Word.
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main() {
    int i,j;
    char str[100];
    char lstr[100];
    scanf("%[^\n]s",&str);
    int len = strlen(str);
    int max = 0; char c;
    int count=1;
    
    for(i=0;i<len;i++){
        lstr[i] = tolower(str[i]);
    }
    
    for(i = 0 ; i<len;i++){
        for(j=i+1;j<len;j++){
            if(lstr[i] == lstr[j]){
                count++;
            }
        }
        if(max<count){
            max = count;
            c = lstr[i];
        }
        count = 1;
    }
    
    printf("%c max repeated times %d",c,max);
    return 0;
}
```

# First Non-duplicate Word
```c

#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main() {
    int i,j;
    char str[100];
    char lstr[100];
    scanf("%[^\n]s",str);
    int len = strlen(str); 
    for(i=0;i<len;i++){
      lstr[i] = tolower(str[i]);
    }
    int flag = 0;
    char ndp[100]; 
    
    for(i = 0;i<len;i++){
        ndp[i] = 0;
    }
    
    for(i=0;i<len;i++){
        for(j=i+1;j<len;j++){
            if(str[i]==str[j]){
                ndp[i] =1;
                ndp[j] =1;
            }
        }
    }
    
    for(i=0;i<len;i++){
        if(ndp[i] == 0){
            printf("%c",str[i]);
            break;
        }
    }
    
    
    return 0;
}
```

# Reverse Words in a String
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void strrev (char word[],int start,int end){
    while(start<end){
        char temp = word[start];
        word[start] = word[end];
        word[end] = temp;
        start++;
        end--;
    }
}

int main() {
    char str[100];
    scanf("%[^\n]",str);
    int len = strlen(str);
    int start = 0;

    for(int i =0;i<=len;i++){
        if(str[i] == ' '|| str[i] == '\0'){
            strrev(str,start,i-1);
            start = i+1;
        }
    }
    
    printf("%s\n",str);
    
    return 0;
}
```
# Find Smallest and Largest Word in a String
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <limits.h>

int main() {
    char str[100];
    scanf("%[^\n]s",str);
    char min_word[50];
    char max_word[50];
    int min_length = INT_MAX;
    int max_length = 0;
    
    int len = strlen(str) ,start =0;
    
    for(int i =0;i<=len;i++){
        
        if(str[i] == ' '|| str[i] =='\0'){
            int word_length = i-start;
            char current_word[50];
            strncpy(current_word,str+start,word_length);
            current_word[word_length] = '\0';
            
            if(word_length < min_length){
                strcpy(min_word,current_word);
                min_length = word_length;
            }
            
            if(word_length > max_length){
                strcpy(max_word,current_word);
                max_length = word_length;
            }
            
            start = i+1;
        }
        
    }
    
    printf("%s\n",min_word);
    printf("%s\n",max_word);

    return 0;
}
```
# Remove Duplicates
```c
#include <stdio.h>
#include <string.h>

int main() {
    char input_string[] = "engineering";
    int seen[256] = {0};  // Array to track seen characters (ASCII range)
    char result[256];     
    int result_index = 0; 

    int length = strlen(input_string);

    for (int i = 0; i < length; i++) {
        char current_char = input_string[i];
	// Check if the current character has been encountered before
        if (!seen[current_char]) {
            result[result_index++] = current_char;
            seen[current_char] = 1;
        }
    }

    result[result_index] = '\0';

    printf("Input: %s\n", input_string);
    printf("Output: %s\n", result);

    return 0;
}

```
# Even Position Words
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d",&n);
    char str[n][10];
    
    for(int i =0;i<n;i++){
        scanf("%s",str[i]);
    }
    
    for(int i = 0 ; i< n; i++){
        if((i+1)%2==0){
            printf("%s ",str[i]);
        }
    }

    return 0;
}
```
# Longest Palindrome Substring
```c
#include <stdio.h>
#include <string.h>

// Function to print the longest palindrome substring
void printLongestPalindromeSubstring(char *s) {
    int length = strlen(s);

    // Initialize a 2D array to store if substring s[i...j] is palindrome
    int dp[length][length];
    memset(dp, 0, sizeof(dp)); // Initialize dp array to 0

    int start = 0; // Start index of the longest palindrome substring found
    int maxLength = 1; // Length of the longest palindrome substring found

    // All substrings of length 1 are palindromes
    for (int i = 0; i < length; i++) {
        dp[i][i] = 1;
    }

    // Check for substrings of length 2
    for (int i = 0; i < length - 1; i++) {
        if (s[i] == s[i + 1]) {
            dp[i][i + 1] = 1;
            start = i;
            maxLength = 2;
        }
    }

    // Check for substrings of length > 2
    for (int len = 3; len <= length; len++) {
        for (int i = 0; i <= length - len; i++) {
            int j = i + len - 1; // Ending index of substring

            // Check if substring s[i...j] is palindrome
            if (s[i] == s[j] && dp[i + 1][j - 1]) {
                dp[i][j] = 1;

                // Update longest palindrome substring found
                if (len > maxLength) {
                    start = i;
                    maxLength = len;
                }
            }
        }
    }

    // Print the longest palindrome substring
    printf("Longest Palindrome Substring: ");
    for (int i = start; i < start + maxLength; i++) {
        printf("%c", s[i]);
    }
    printf("\n");
}

int main() {
    char input_string[] = "bananas";

    // Find and print the longest palindrome substring
    printLongestPalindromeSubstring(input_string);

    return 0;
}

```
# "23:24:09" - Hours:23 Minutes:24 Seconds:9
```c
#include <stdio.h>
#include <string.h>

// Function to convert a string of digits to an integer
int stringToInt(char *str) {
    int result = 0;
    int len = strlen(str);

    for (int i = 0; i < len; i++) {
        result = result * 10 + (str[i] - '0'); // Convert character to integer
    }

    return result;
}

int main() {
    char input_string[] = "23:24:09";
    char hours_str[3], minutes_str[3], seconds_str[3];
    int hours, minutes, seconds;

    // Parse the input time string
    sscanf(input_string, "%2s:%2s:%2s", hours_str, minutes_str, seconds_str);

    // Convert the parsed strings to integers
    hours = stringToInt(hours_str);
    minutes = stringToInt(minutes_str);
    seconds = stringToInt(seconds_str);

    // Output the formatted time
    printf("Hours : %d Minutes : %d Seconds : %d\n", hours, minutes, seconds);

    return 0;
}

```
# Swap Adjacent Characters
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>

int main()
{
    char str[20]; 
    scanf(" %[^\n]",str);
    
    int len = strlen(str);
    
    for(int i = 0;str[i] != '\0';i+=2){
        while (isspace(str[i])) {
            i++;
        }
        if (isspace(str[i + 1])) {
            i++;
        }
        char temp = str[i];
        str[i] = str[i+1];
        str[i+1] =temp;
    }
    
    printf("%s\n",str);
    
}

-------------------------- with odd string 👇--------------------------------
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char str[50];
    scanf("%[^\n]", str);
    int len = strlen(str);
    int start = 0;
    
    while (start <len){
        while(start < len && isspace(str[start])) start++;
        
        int end = start;
        while (end<len && !(isspace(str[end]))) end++;
        
        for(int i=start ; i<end-1;i+=2){
            char temp = str[i];
            str[i] =str[i+1];
            str[i+1] =temp;
        }
        start = end;
        
    }
    
    printf("%s\n", str);
    return 0;
}

```
# Character count and check for odd even prime
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>

int isprime(int n){
    if(n ==0 || n == 1) return 0; 
    
    for(int i = 2;i<=n/2;i++){
        if(n%i==0){
            return 0;
        }
    }
    return 1;
}

int main(){
    int count = 0;
    char str[100];
    scanf("%[^\n]",str);
    
    int len = strlen(str);
    
    for (int i = 0;i<len;i++){
        if(!isspace(str[i])) count++;
    }
    printf("%d\n",count);
    
    if(isprime(count) && count%2 != 0){ printf("prime and Odd");}
    else if(isprime(count)){ printf("prime");}
    else if(count % 2 != 0) printf("Odd");
    if(count % 2 ==0){
        printf("even");
    }
    
}
```
# Vowel Counter in a string
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>

int main(){
   int count = 0;
   char str[100];
   scanf("%[^\n]s",str);
   int len = strlen(str);
   char lstr[100];
   
   for(int i = 0 ;i<=len;i++){
       count++;
       lstr[i] = tolower(str[i]);
   }
      lstr[count] = '\0';
   printf("%s\n",lstr);
   count = 0;
   
   for(int i = 0 ; i<len;i++){
       if(lstr[i] == 'a' || lstr[i] == 'e' || lstr[i] == 'i' || lstr[i] == 'o' || lstr[i] == 'u' ){
           count ++;
       }
   }
   printf("%d",count);
    
}
```
# Remove The punctuations
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>


int main()
{
    char str[50];
    scanf("%[^\n]",str);
    char result[50];
    int res = 0;
    int len = strlen(str);
    
    for(int i = 0 ;i<len;i++){
        if(!(ispunct(str[i]))){
            result[res++] = str[i];
        }
    }

    printf("%s\n",result);

}
```
# Anagram
```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

void sortString(char* str) {
    int len = strlen(str);
    for (int i = 0; i < len - 1; i++) {
        for (int j = i + 1; j < len; j++) {
            if (str[i] > str[j]) {
                char temp = str[i];
                str[i] = str[j];
                str[j] = temp;
            }
        }
    }
    
    printf("%s\n",str);
}

bool areAnagrams(char* str1, char* str2) {
    // If lengths are not equal, they cannot be anagrams
    if (strlen(str1) != strlen(str2)) {
        return false;
    }

    // Sort both strings
    sortString(str1);
    
    sortString(str2);

    // Compare the sorted strings
    return strcmp(str1, str2) == 0;
}

int main() {
    char str1[100];  // Increase size to accommodate larger strings
    char str2[100];  // Increase size to accommodate larger strings

    printf("Enter first string: ");
    scanf("%99s", str1);  // Use %99s to avoid buffer overflow
    printf("Enter second string: ");
    scanf("%99s", str2);  // Use %99s to avoid buffer overflow

    if (areAnagrams(str1, str2)) {
        printf("Anagram\n");
    } else {
        printf("Not Anagram\n");
    }

    return 0;
}
**

#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <stdlib.h>

void sortstring(char* str){
    int len = strlen(str);
    for (int i=0;i<len;i++){
        for(int j=i+1;j<len;j++){
            if(str[i]>str[j]){
                char temp = str[i];
                str[i] = str[j];
                str[j] = temp;
            }
        }
    }
}

int main() {
    char str1[100];
    char str2[100];
    scanf("%[^\n]s", str1);
    getchar();
    scanf("%[^\n]s", str2);
    getchar();
    int l1 = strlen(str1);
    int l2 = strlen(str2);
    for (int i = 0; i < l1; i++) {
        str1[i] = tolower(str1[i]);
    }

    for (int i = 0; i < l2; i++) {
        str2[i] = tolower(str2[i]);
    }
    sortstring(str1);
    sortstring(str2);
    int i = strcmp(str1,str2);
    if(i==0){
        printf("Anagram");
    }else{
        printf("Not Anagram");
    }


    return 0;
}

```
# Greatest English Letter in Upper and Lower Case
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char str[100];
    scanf("%[^\n]s", str);
    int len = strlen(str);
    
    for (char c = 'Z'; c >= 'A'; c--) {
        int found_upper = 0;
        int found_lower = 0;
        
        for (int i = 0; i < len; i++) {
            if (str[i] == c) {
                found_upper = 1;
            }
            if (str[i] == tolower(c)) {
                found_lower = 1;
            }
            if (found_upper && found_lower) {
                printf("%c\n", c);
                return 0;
            }
        }
    }
    
    return 0;
}

```
# Valid Parentheses
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isValid(char* s) {
    int len = strlen(s);
    char stack[len];
    int top = -1;
    
    for (int i = 0; i < len; i++) {
        if (s[i] == '(' || s[i] == '{' || s[i] == '[') {
            stack[++top] = s[i];
        } else {
            if (top == -1) return false;
            if (s[i] == ')' && stack[top] != '(') return false;
            if (s[i] == '}' && stack[top] != '{') return false;
            if (s[i] == ']' && stack[top] != '[') return false;
            top--;
        }
    }
    
    return top == -1;
}

int main() {
    char str[100];
    scanf("%s", str);
    
    if (isValid(str)) {
        printf("true\n");
    } else {
        printf("false\n");
    }
    
    return 0;
}

```
# Minimum Length of String After Deleting Similar Ends.
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%s", str);
    int len = strlen(str);

    int left = 0;
    int right = len - 1;

    while (left < right && str[left] == str[right]) {
        char current_char = str[left];
        while (left <= right && str[left] == current_char) {
            left++;
        }
        while (left <= right && str[right] == current_char) {
            right--;
        }
    }

    int result = right - left + 1;
    printf("%d\n", result);

    return 0;
}

```
# FLAMES
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Function to remove common characters and count remaining characters
int count_remaining_chars(char *str1, char *str2) {
    int count[26] = {0};
    int len1 = strlen(str1);
    int len2 = strlen(str2);
    int remaining = 0;

    // Convert all characters to uppercase for consistency
    for (int i = 0; i < len1; i++) {
        str1[i] = toupper(str1[i]);
    }
    for (int i = 0; i < len2; i++) {
        str2[i] = toupper(str2[i]);
    }

    // Count occurrences of each character in str1
    for (int i = 0; i < len1; i++) {
        if (str1[i] >= 'A' && str1[i] <= 'Z') {
            count[str1[i] - 'A']++;
        }
    }

    // Subtract occurrences of each character in str2
    for (int i = 0; i < len2; i++) {
        if (str2[i] >= 'A' && str2[i] <= 'Z') {
            count[str2[i] - 'A']--;
        }
    }

    // Calculate the remaining characters count
    for (int i = 0; i < 26; i++) {
        remaining += abs(count[i]);
    }

    return remaining;
}

// Function to determine the FLAMES result
char get_flames_result(int count) {
    char flames[] = "FLAMES";
    int len = strlen(flames);
    int pos = 0;

    // Loop to eliminate characters based on count
    while (len > 1) {
        pos = (pos + count - 1) % len;
        for (int i = pos; i < len - 1; i++) {
            flames[i] = flames[i + 1];
        }
        len--;
    }

    return flames[0];
}

int main() {
    char player1[100], player2[100];

    printf("Enter name of Player 1: ");
    scanf("%s", player1);

    printf("Enter name of Player 2: ");
    scanf("%s", player2);

    int remaining_count = count_remaining_chars(player1, player2);
    char result = get_flames_result(remaining_count);

    printf("Result = '%c'\n", result);

    return 0;
}

```obs