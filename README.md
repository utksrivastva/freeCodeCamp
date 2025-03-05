# freeCodeCamp

## Coding Interview Prep
- Find the symmetric difference

      The mathematical term symmetric difference (△ or ⊕) of two sets is the set of elements which are in either of the two sets but not in both. For example, for sets A = {1, 2, 3} and B = {2, 3, 4}, A △ B = {1, 4}.
      
      Symmetric difference is a binary operation, which means it operates on only two elements. So to evaluate an expression involving symmetric differences among three elements (A △ B △ C), you must complete one operation at a time. Thus, for sets A and B above, and C = {2, 3}, A △ B △ C = (A △ B) △ C = {1, 4} △ {2, 3} = {1, 2, 3, 4}.
      
      Create a function that takes two or more arrays and returns an array of their symmetric difference. The returned array must contain only unique values (no duplicates).

     ```JavaScript
            /**
       * Calculates the symmetric difference between two arrays.
       * @param {Array} arr1 - First array.
       * @param {Array} arr2 - Second array.
       * @returns {Array} - Array with elements in either arr1 or arr2 but not both.
       */
      function symmetricDifferenceTwoArrays(arr1, arr2) {
        // Create sets from the arrays to automatically handle duplicates
        const set1 = new Set(arr1);
        const set2 = new Set(arr2);
        
        // Elements in arr1 that are not in arr2
        const diff1 = [...set1].filter(item => !set2.has(item));
        
        // Elements in arr2 that are not in arr1
        const diff2 = [...set2].filter(item => !set1.has(item));
        
        // Combine the differences
        return [...diff1, ...diff2];
      }
      
      /**
       * Calculates the symmetric difference of two or more arrays.
       * @param {...Array} arrays - Two or more arrays to find symmetric difference.
       * @returns {Array} - Array containing only unique values present in an odd number of input arrays.
       */
      function sym(...arrays) {
        // Check if we have at least two arrays
        if (arrays.length < 2) {
          return arrays.length === 1 ? [...new Set(arrays[0])] : [];
        }
        
        // Start with the first array
        let result = [...new Set(arrays[0])];
        
        // Process each subsequent array
        for (let i = 1; i < arrays.length; i++) {
          result = symmetricDifferenceTwoArrays(result, arrays[i]);
        }
        
        return result;
      }
      
      // Test cases
      console.log(sym([1, 2, 3], [2, 3, 4])); // [1, 4]
      console.log(sym([1, 2, 3], [2, 3, 4], [2, 3])); // [1, 2, 3, 4]
      console.log(sym([1, 2, 3, 3], [5, 2, 1, 4], [2, 1])); // [3, 4, 5]
      console.log(sym([1, 1, 2, 5], [2, 2, 3, 5], [3, 4, 5, 5])); // [1, 4, 5]
   ```

- No repeats please

        Return the number of total permutations of the provided string that don't have repeated consecutive letters. Assume that all characters in the provided string are each unique.
      
      For example, aab should return 2 because it has 6 total permutations (aab, aab, aba, aba, baa, baa), but only 2 of them (aba and aba) don't have the same letter (in this case a) repeating.
