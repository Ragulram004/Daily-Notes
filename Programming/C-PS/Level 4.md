Topic : Strings
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
    scanf("%s", player1);
    scanf("%s", player2);

    int remaining_count = count_remaining_chars(player1, player2);
    char result = get_flames_result(remaining_count);

    printf("Result = '%c'\n", result);

    return 0;
}

```
# Kth Distinct String in an Array
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int isdistinct(char arr[][10],int size, int k){
    int count=0;
    for (int i =0;i<size;i++){
        if(strcmp(arr[i],arr[k]) == 0){
            count++;
        }
    }
    return count == 1;
}

char* kthdistinct(char arr[][10],int size,int k){
    int distinctcount =0;
    for (int i=0;i<size;i++){
        if(isdistinct(arr,size,i)){
            distinctcount++;
            if(distinctcount == k){
                return arr[i];
            }
        }
    }
    return "";
}

int main() {
    int n;
    scanf("%d",&n);
    char arr[n][10];
    for (int i=0;i<n;i++){
        scanf("%s",arr[i]);
    }
    int k;
    scanf("%d",&k);
    
    char* result = kthdistinct(arr,n,k);
    if(strlen(result) == 0){
        printf("\"\"");
    }else{
        printf("%s",result);
    }
    
    return 0;
}
```
# String-Roman to Integer
```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

// Function to get the integer value of a Roman numeral character
int romanToInt(char c) {
    switch(c) {
        case 'I': return 1;
        case 'V': return 5;
        case 'X': return 10;
        case 'L': return 50;
        case 'C': return 100;
        case 'D': return 500;
        case 'M': return 1000;
        default: return -1;
    }
}

bool isValidRomanNumeral(char *s) {
    for (int i = 0; s[i] != '\0'; i++) {
        if (romanToInt(s[i]) == -1) {
            return false;
        }
    }
    return true;
}

int convertRomanToInt(char *s) {
    int total = 0;
    int prevValue = 0;
    int currentValue = 0;
    
    for (int i = strlen(s) - 1; i >= 0; i--) {
        currentValue = romanToInt(s[i]);
        if (currentValue < prevValue) {
            total -= currentValue;
        } else {
            total += currentValue;
        }
        
        prevValue = currentValue;
    }
    
    return total;
}

int main() {
    char s[20];
    scanf("%s", s);
    if (!isValidRomanNumeral(s)) {
        printf("Error: Invalid Roman numeral input.\n");
        return 1;
    }
    int result = convertRomanToInt(s);
    printf("Output: %d\n", result);

    return 0;
}
```
# Longest Palindrome Substring
```c
#include <stdio.h>
#include <string.h>

int ispali(int i, int j,char *str){
    while (i <= j) {
        if (str[i] != str[j]) {
            return 0;
        }
        i++;
        j--;
    }
    return 1;
}

int main() {
    char str[100];
    scanf("%s",str);
    int len = strlen(str);
    char max[100];
    for(int i=0;i<len;i++){
        for(int j =i+1;j<len;j++){
            if(ispali(i,j,str)){
                int m = strlen(max);int count =0;
                for(int k =i;k<=j;k++){
                    count++;
                }
                if(m<count){
                    for(int l = 0;l<count;l++){
                        max[l] = str[i++];
                    }
                }
            }
        }
    }
    
    printf("%s",max);

    return 0;
}
```
# Ransom Note
```c
#include<stdio.h>
#include<string.h>

int ramsonNote(char *ramson,char* magzine){
    int magcount[26] = {0};
    
    for(int i =0;magzine[i] !='\0';i++){
        magcount[magzine[i]-'a']++;
    }
    for(int i =0;ramson[i] != '\0';i++){
        if(magcount[ramson[i]-'a'] == 0){
            return 0;
        }
        magcount[ramson[i]]--;
    }
    return 1;
    
}

int main(){
    char ramson[100];
    scanf("%s",ramson);
    char magzine[100];
    scanf("%s",magzine);
    
    if( ramsonNote(ramson,magzine)){
        printf("True");
    }else{
        printf("False");
    }
}
```
# Second Largest Element in a String
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

void seclar(char *s){
    int digits[10] = {0}; 

    for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            digits[s[i] - '0']++;
        }
    }

    int firstLargest = -1;
    int secondLargest = -1;

    for (int i = 9; i >= 0; i--) {
        if (digits[i]) {
            if (firstLargest == -1) {
                firstLargest = i;
            } else if (secondLargest == -1) {
                secondLargest = i;
                printf("%d",secondLargest);
                exit(0);
            }
        }
    }
}

int main() {
    char str[100];
    scanf("%s",str);
    int len = strlen(str);
    
    seclar(str);


    return 0;
}
```
# Make Three Strings Equal by deleting rightmost element
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int right(char* s1, char* s2, char* s3 ){
    int l1 = strlen(s1);
    int l2 = strlen(s2);
    int l3 = strlen(s3);
    
    int i = l1-1;
    int j = l2-1;
    int k = l3-1;
    int operation = 0;
    
    while(i>=0 && j>=0 && k>=0){
        if(s1[i] == s2[j] && s2[j] == s3[k]){
            i--;j--;k--;
        }else{
            if(i>=j && i>=k){
                i--;
            }else if(j>=i && j>=k){
                j--;
            }else{
                k--;
            }
            operation++;
        }
    }
    return operation;
}

int main(){
    char s1[100];
    char s2[100];
    char s3[100];
    scanf("%s",s1);
    scanf("%s",s2);
    scanf("%s",s3);

    if(strcmp(s1,s2)==0 && strcmp(s2,s3)==0){
        printf("0");
    }else{
        int result = right(s1,s2,s3);
            if(result != -1){
                printf("%d",result);
            }else{
                printf("-1");
            }
        
    }
}
```
# First non repeated character and last repeated character in a word.
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    char s[100];
    scanf("%s", s);
    int len = strlen(s);

    char first_non_repeated = '\0';
    for (int i = 0; i < len; i++) {
        int flag = 1;
        for (int j = 0; j < len; j++) {
            if (i != j && s[i] == s[j]) {
                flag = 0;
                break;
            }
        }
        if (flag) {
            first_non_repeated = s[i];
            break;
        }
    }
    if (first_non_repeated != '\0') {
        printf("First_non_repeated: %c\n", first_non_repeated);
    } else {
        printf("First_non_repeated: None\n");
    }

    char last_repeated = '\0';
    for (int i = len - 1; i >= 0; i--) {
        for (int j = i - 1; j >= 0; j--) {
            if (s[i] == s[j]) {
                last_repeated = s[i];
                break;
            }
        }
        if (last_repeated != '\0') {
            break;
        }
    }
    if (last_repeated != '\0') {
        printf("Last_repeated: %c\n", last_repeated);
    } else {
        printf("Last_repeated: None\n");
    }

    return 0;
}

```
# Valid Email
```c
// Online C compiler to run C program online
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

 int isValid(char* s){
     int len = strlen(s);
     int atcount =0;
     int atindex = -1;
     int dotcount =0;
     
     if(len<3){
         return 0;
     }
     
     for (int i=0;i<len;i++){
         if(s[i] == '@'){
             atcount++;
             atindex = i;
         }
     }
     
     if(atcount != 1){
         return 0;
     }
     if(atindex == 0 || atindex == len-1){
         return 0;
     }
     for(int i = atcount+1;i<len;i++){
         if(s[i]=='.'){
             dotcount++;
         }
     }
    if(dotcount == 0){
        return 0;
    }
     
    if(s[atcount+1]=='.' || s[len-1] == '.'){
        return 0;
    }

    return 1;
     
 }


int main() {
    char s[100];
    scanf("%s",s);    
    int result = isValid(s);
    if(result){
        printf("Valid");
    }else{
        printf("InValid");
    }

    return 0;
}
```
# Count the occurrence of special characters in the given string.
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>

#define MAX_CHAR 256

void count(char* s){
    int count[MAX_CHAR] ={0};
    for(int i =0;i< strlen(s);i++){
        if(!isalnum(s[i]) && !isspace(s[i])){
            count[s[i]]++;
        }
    }
    
    for(int i=0;i<MAX_CHAR;i++){
        if(count[i] > 0 && !isalnum(i) && !isspace(i)){
            printf("%c : %d \n",i,count[i]);
        }
    }
}


int main(){
    char s[100];
    scanf("%[^\n]s",s);
    
    count(s);
    
    
}

-------------------------------------------
#include<stdio.h>
#include<string.h>
#include<ctype.h>


int main(){
    char s[100];
    scanf("%[^\n]s",s);
    int len = strlen(s);
    
    for(int i =0;i<len;i++){
      if(!isalnum(s[i]) && !isspace(s[i])){
          int count =1;
          for(int j=i+1;j<len;j++){
              if(s[i] == s[j]){
                  count++;
                  s[j] = s[j+1];
                  len--;
              }
          }
          printf("%c : %d \n",s[i],count);
          s[i] = s[i+1];
      }  
    }
}
```
# Remove the left along with*
```c
#include <stdio.h>
#include <string.h>

void processString(char *input, char *output) {
    int j = 0;
    int n = strlen(input);
    
    for (int i = 0; i < n; i++) {
        if (input[i] == '*') {
            if (j > 0) {
                j--;
            }
        } else {
            output[j++] = input[i];
        }
    }
    output[j] = '\0';
}

int main() {
    char input[100];
    char output[100];

    printf("Enter the input string: ");
    scanf("%[^\n]s",input);

    processString(input, output);

    printf("Processed output: \"%s\"\n", output);

    return 0;
}

```
# Words to integer

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// Helper function to map number words to their corresponding integer values
int wordToNumber(const char* word) {
    if (strcmp(word, "Zero") == 0) return 0;
    if (strcmp(word, "One") == 0) return 1;
    if (strcmp(word, "Two") == 0) return 2;
    if (strcmp(word, "Three") == 0) return 3;
    if (strcmp(word, "Four") == 0) return 4;
    if (strcmp(word, "Five") == 0) return 5;
    if (strcmp(word, "Six") == 0) return 6;
    if (strcmp(word, "Seven") == 0) return 7;
    if (strcmp(word, "Eight") == 0) return 8;
    if (strcmp(word, "Nine") == 0) return 9;
    if (strcmp(word, "Ten") == 0) return 10;
    if (strcmp(word, "Eleven") == 0) return 11;
    if (strcmp(word, "Twelve") == 0) return 12;
    if (strcmp(word, "Thirteen") == 0) return 13;
    if (strcmp(word, "Fourteen") == 0) return 14;
    if (strcmp(word, "Fifteen") == 0) return 15;
    if (strcmp(word, "Sixteen") == 0) return 16;
    if (strcmp(word, "Seventeen") == 0) return 17;
    if (strcmp(word, "Eighteen") == 0) return 18;
    if (strcmp(word, "Nineteen") == 0) return 19;
    if (strcmp(word, "Twenty") == 0) return 20;
    if (strcmp(word, "Thirty") == 0) return 30;
    if (strcmp(word, "Forty") == 0) return 40;
    if (strcmp(word, "Fifty") == 0) return 50;
    if (strcmp(word, "Sixty") == 0) return 60;
    if (strcmp(word, "Seventy") == 0) return 70;
    if (strcmp(word, "Eighty") == 0) return 80;
    if (strcmp(word, "Ninety") == 0) return 90;
    if (strcmp(word, "Hundred") == 0) return 100;
    if (strcmp(word, "Thousand") == 0) return 1000;
    if (strcmp(word, "Million") == 0) return 1000000;
    if (strcmp(word, "Billion") == 0) return 1000000000;
    return -1; // For any unknown word
}

// Function to convert the string to a number
int stringToNumber(char* input) {
    char* token;
    int result = 0;
    int current = 0;
    int multiplier = 0;

    token = strtok(input, " ");
    while (token != NULL) {
        int number = wordToNumber(token);
        if (number == 100) {
            current *= number;
        } else if (number >= 1000) {
            current *= number;
            result += current;
            current = 0;
        } else if (number > 0) {
            current += number;
        }
        token = strtok(NULL, " ");
    }
    result += current;
    return result;
}

int main() {
    char input[1000];
   
   scanf("%[^\n]s",input);
   printf("%d",stringToNumber(input));
   
    return 0;
}
```


