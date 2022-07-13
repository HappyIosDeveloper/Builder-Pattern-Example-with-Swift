# Builder Pattern Example with Swift

## Run the folllwing code on the Playground


import Foundation

struct Car {
    
    var ownerName: String?
    var numberOfSeets: Int?
    var numberOfDoors: Int?
    var color: CarColor?
    
    enum CarColor { case red, blue, white, black }
}

class CarBuilder {
    
    var car: Car?
    
    init(car: Car?) {
        self.car = car
    }
    
    func Build()-> Car? {
        guard let car = car else { return nil }
        if let onn = car.ownerName, let nus = car.numberOfSeets, let nod = car.numberOfDoors, let col = car.color {
            return Car(ownerName: onn, numberOfSeets: nus, numberOfDoors: nod, color: col)
        }
        return nil
    }
}

let newCar = CarBuilder(car: Car(ownerName: "Ahmad"))
if let car = newCar.Build() {
    print("we have a complete car: \(car)")
}

// MARK: - Another example
/**
 Swift URL component also uses this technique to create a URL step by step!
 */
var component = URLComponents()
component.scheme = "https"
component.host = "google.com/search/image"
component.queryItems = [URLQueryItem(name: "q", value: "cat")]
let url = component.url
print(url!.absoluteString) // https://www.google.com/search?q=cat


// MARK: another example use case is for a register form or any data we want to collect and send or use.
