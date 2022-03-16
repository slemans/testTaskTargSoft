# Test task for company TargSoft
<img src="https://camo.githubusercontent.com/467ed139385667771e9fe3da0e60ece0d4ec64128a76e8a515e57aecfddf765e/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f73776966742d352d627269676874677265656e2e7376673f7374796c653d666c6174" alt="Language" data-canonical-src="https://img.shields.io/badge/swift-5-brightgreen.svg?style=flat" style="max-width: 100%;">
<h2>Given two arrays, array1 and array2, find which elements in array2 are not present in array1.</h2>
<ul>
  <li>If an element occurs multiple times in the lists, you must ensure that the frequency of that element in both lists is the same. If that is not the case, then it is also a missing element.</li>
  <li>Return the missing elements sorted ascending.</li>
  <li>Only include a missing element once, even if it is missing multiple times.</li>
  <li>Your code should be able to handle any type which can be equated (i.e., ==), sorted and (optionally) hashed. For example: numbers, strings, custom types, etc.</li>
  <li>Do not write an entire application or use multiple files. Write code which can be pasted together into a playground and run as is.</li>
  <li>You may have as many helper functions as you like, but you must have one main function called solve which takes the two arrays (of any conforming type!) as parameters and returns the expected result. You may not overload solve.</li>
  <li>While examples are given below for both Swift and Kotlin, write your code in the language of the job for which you are applying. Use these examples to test your code. They are correct.
</li>
  <li>You may use any collection types you wish, as long as the answer is correct: List, Array, Set, etc. Whatever works. Thus, the (pseudocode) definition of your function could be solve(List, List) -> List or solve(Array, Set) -> List.</li>
  <li>Write type-safe code. Do not use metaprogramming, reflection, or types such as Any.
</li>
  <li>Efficiency and speed are not important. Solving the problem correctly is important.</li>
  <li>Although solving the problem correctly is the most important consideration, the second most important are brevity and concision. Keep your solution as small as possible without sacrificing good style and clarity, but don't overthink it.</li>
  <li>Do the work yourself. We will be discussing your solution in your interview, so be prepared to explain it.</li>
  <li>Provide your solution as a Gist on GitHub and send the link to your interview contact at Patron so the engineering team can review it.</li>
  <li>Do not leave comments on this Gist. They will be deleted.</li>
</ul>
<h2>Answer Swift)</h2>


```swift
func solve2<T: Hashable>(_ arrayOne: [T], _ arrayTwo: [T]) -> [T] where T: Comparable {
    var arrayMain: [T] = []
    func createDictionary(_ array: [T]) -> [T: [Int]] {
        var dictionary = [T: [Int]]()
        for number in 0 ..< array.count {
            var arrayNew = [Int]()
            let element = array[number]
            for item in array {
                if item == element {
                    arrayNew.append(number)
                }
            }
            dictionary.updateValue(arrayNew, forKey: element)
        }
        return dictionary
    }
    let dictionaryOne = createDictionary(arrayOne)
    let dictionaryTwo = createDictionary(arrayTwo)

    dictionaryTwo.forEach { (number, array) in
        let element = number
        let count = array.count
        let arrayOne = dictionaryOne[element]
        if (arrayOne?.count != count) {
            arrayMain.append(element)
        }
    }
    return arrayMain.sorted(by: <)
}
```
