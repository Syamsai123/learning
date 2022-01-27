import time
class Book:
    #Storing The Movie name price and ticket available in a Dictionaries
    tic_details={'Avengers':[100,500],
        'Ant-man':[26,450],'Spider-man':[40,600]}
    def _init_(self) :
        print("\tTicket Details")
        print("-----------------------------")
        print("\tAvailable movies are: \n")
        for movies in self.tic_details.keys():
            print(f"||Movie Name:{movies}| |Available Tickets:{self.tic_details[movies][0]}| |Price Per Ticket:{self.tic_details[movies][1]}") 

    def getDetails(self):
        self.chosenMov=input("Enter the Name Of the Movie: ").capitalize()
        self.viewers=int(input("Enter The Number of Viewers: "))

    def checkAvailable(self):
        if self.chosenMov in self.tic_details:
            return True
        else:
            return False
    def bookTicket(self):
        try:
            self.price=self.tic_details[self.chosenMov][1]*self.viewers
            # print(f"Your Have paid:{self.price}")
        except Exception as e:
            print("Error")
       
    def getPayment(self):
        pass
        print("Conforming The Payment...")
        time.sleep(2)
        print("Payment Successful...")
        time.sleep(1)
        print("Thanks For Choosing Us ")
        return True
    def update(self):
        self.tic_details[self.chosenMov][0]-=self.viewers
        print(f"The Remaining Tickets for {self.chosenMov} is {self.tic_details[self.chosenMov][0]}")
        # print(self.price)
        # print("Updated The Local Database")
    def getTicket(self):
        print("-----------------------------------")
        print("\tYour Ticket Is Here")
        print("-----------------------------------")
        print(f"Movie Name:{self.chosenMov}\nNumber Of Viewers:{self.viewers}\nTiming:Your-Timing-Here\nYou Paid:{self.price}")

    def storeDetail(self):
        upcoming=open("Upcoming Plan.txt","a")
        upcoming.write(str(self.chosenMov)+"\n")
        upcoming.write(str(self.viewers)+"\n")
        upcoming.write(str(self.price)+"\n")
        # print("Added")

print("\tBook A Ticket")
print("***********")

obj=Book()
obj.getDetails()
available=obj.checkAvailable()
if available:
    isPaid=obj.getPayment()
    if isPaid:
        time.sleep(5)
        obj.bookTicket()
        time.sleep(0.1)
        obj.update()
        time.sleep(0.1)
        obj.getTicket()
        time.sleep(0.1)
        obj.storeDetail()
    else:
        time.sleep(0.2)
        print("Payment Faild!")
        print("Please Try Again!!")
else:
    print("The Movie is not available at the moment")
