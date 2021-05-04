//Allows use to use the Swift pow() method
import Foundation

//Calculates the mod (i.e a^(p-1) % p)
//Note: (x.y) mod p == ((x mod p).(y mod p)) mod p
//Completes in O(log N) time
func powmod(_ a: Int, _ x: Int, _ m: Int) -> Int { // O(log N)
    //Base Case: exponent is 1 or 2, if 1 return a^1 % m, else a^2 % m
    guard x > 2 else {
        let res = a % m
        if x == 1 { return res }
        return (res * res) % m
    }

    //Reduce the ammount of work in half by dividing exponent by 2 and passing to powmod() to get a result
    let res = powmod(a, x/2, m)
    if x & 1 == 0 { // x even
        //If the exponent was even (i.e a^2n % m == ( (a^n % m) * (a^n % m) ) % m ...in this case a^n % m is result of powmod(a,x/2,m) in res)
        return (res * res) % m
    } else { // x odd
        //If exponent was odd (i.e a^(2n+1) % m == ( (a^1 % m) * (a^n % m) * (a^n % m) ) % m == ( a * (a^n % m) * (a^n % m) ) % m since a is always less than m)
        return (a * res * res) % m
    }
}

//Checks primality (i.e a^(p-1) % p == 1)
//a -> a random number greater than 1 and less than the number to be tested
//Note: a^(p-1) = 1 (mod p)  for any prime number
//Completes in constant time
func isProbablyPrime(_ p : Int) -> Bool { // O(1)
    return powmod(Int.random(in: 1..<p), p-1, p) == 1
}

//Defines the upper limit on the range of numbers we can test (i.e the cuberoot of Int.max which equates to 2,097,151 in my computer)
let limit = Int(pow(Double(Int.max), 1.0/3.0))
//Stores the probable primes
var primes: [Int] = []
//Test for primality on numbers ranging from 2 to `limit`.
//Completes in O(N) time
let start = Date()
for i in 2..<limit {
    if isProbablyPrime(i) { // O(N)
        primes.append(i)
    }
}
let finish = Date()

let diffComponents = Calendar.current.dateComponents([.hour, .minute, .second, .nanosecond], from: start, to: finish)
let hours = diffComponents.hour
let minutes = diffComponents.minute
let seconds = diffComponents.second
let nanosecond = diffComponents.nanosecond
print("Duration: Hrs: \(hours ?? 0) Mins: \(minutes ?? 0) Sec: \(seconds ?? 0) Nanosecond: \(nanosecond ?? 0)")

//Prints out the array of probable prime numbers
print(primes)
