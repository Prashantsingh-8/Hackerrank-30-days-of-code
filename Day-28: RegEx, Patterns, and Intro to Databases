#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>
#include <ctype.h>

int mycmp(const char *a, const char *b) {
    const char *cp1 = a, *cp2 = b;

    for (; toupper(*cp1) == toupper(*cp2); cp1++, cp2++)
        if (*cp1 == '\0')
            return 0;
    return ((toupper(*cp1) < toupper(*cp2)) ? -1 : +1);
} 

int cmp(const void *p1, const void *p2) {
    return mycmp(* (char * const *) p1, * (char * const *) p2);
}

char* validate_local_address(char* email) {
    char *ptr;
    for (ptr = email; *ptr; ptr++) {
        if (*ptr == '@' && ptr != email) {
            // check that we saw at least one character
            return ptr+1;
        } else if (!((*ptr >= 'a' && *ptr <= 'z') || (*ptr == '.'))) {
            return 0;
        }
    }
    return 0;
}

int main(){
    int N; 
    scanf("%d",&N);
    char **result = (char **)malloc(N * sizeof(char *));
    int index = 0;
    for(int a0 = 0; a0 < N; a0++){
        char* firstName = (char *)malloc(1024 * sizeof(char));
        memset(firstName, 0, 1024);
        
        char* emailID = (char *)malloc(1024 * sizeof(char));
        memset(emailID, 0, 1024);
        
        scanf("%s %s",firstName,emailID);
        int len = strlen(emailID);
        if (strlen(firstName)) {
            char *ptr = validate_local_address(emailID);
            if (ptr) {
                if (!strcmp(ptr, (const char *)"gmail.com")) {
                    char *p = firstName;
                    for ( ; *p; ++p) *p = tolower(*p);
                    result[index++] = firstName;
                }
            }
        }
    }
    
    if (index) {
        // sort the names alphabetically
        qsort(result, index, sizeof(char *), cmp);
        
        int i;
        for (i = 0; i < index; i++) {
            printf("%s\n", result[i]);
        }
    }
    
    return 0;
}
