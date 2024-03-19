# QAP-4-Files-LM

# Description: Program for One Stop Insurance Company to calculate new insurance policy information for its customers
# Author: Luke Metcalfe
# Date: March 14, 2024


# import libraries
import FormatValues as FV
import datetime
import time
import sys


# Define program constants
# Open default values
f = open('Def.dat', 'r')
POLICY_NUM = int(f.readline())
BASIC_PREM = float(f.readline())
ADD_CAR_DIS = float(f.readline())
EXTRA_LIBILITY_COV = float(f.readline())
GLASS_COV = float(f.readline())
LOAN_CAR_RATE = float(f.readline())
HST_RATE = float(f.readline())
PROCESSING_FEE = float(f.readline())
f.close()


CURR_DATE = datetime.datetime.now()

# Define program functions
def CustomerClaims():
    while True:

       



        while True:
            global ClaimNumLst
            ClaimNumLst = []    
            try:
                global ClaimNum
               

                ClaimNum = input("Enter the claim number: ")
                ClaimNum = int(ClaimNum)
                ClaimNumLst.append(ClaimNum)
            except:
                print("Data Entry Error - claim number is not a valid number.")
            else:
                if ClaimNum == "":
                    print("Data Entry Error - claim number cannot be blank.")
                else:
                    break
            

        allowed_claim_date_char = set("1234567890-")
        while True:
            global ClaimDateLst
            ClaimDateLst = []
            global ClaimDate

            ClaimDate = input("Enter the claim Date (YYYY-MM-DD): ")
            ClaimDateLst.append(ClaimDate)

            if ClaimDate == "":
                print("Data Entry Error - claim date cannot be blank.")
            elif set(ClaimDate).issubset(allowed_claim_date_char) == False:
                print("Data Entry Error - claim date contains invalid characters.")
            else:
                break
            

        while True:
            global ClaimAmtLst
            ClaimAmtLst = []
            try:
                global ClaimAmt

                ClaimAmt = input("Enter the claim amount: ")
                ClaimAmt = float(ClaimAmt)
                ClaimAmtLst.append(ClaimAmt)
            except:
                print("Data Entry Error - claim amount is not a valid amount.")
            else:
                if ClaimAmt == "":
                    print("Data Entry Error - claim amount cannot be blank.")
                else:
                    break

        while True:
            Continue = input("Would you like to process another claim? (Y/N): ")
            
            if Continue != "Y" and Continue != "N":
                print("Data Entry Error - Must enter either Y or N.")
            else:
                break
        if Continue == "N":
            break
        
   
   



# Main program

while True:
    # Gather user inputs
    
    allowed_cust_first_name_char = set("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz-.,'")
    while True:
        CustFirstName = input("Enter the Customers first name: ").title()

        if CustFirstName == "":
            print("Data Entry Error - Customer first name cannot be blank.")
        elif set(CustFirstName).issubset(allowed_cust_first_name_char) == False:
            print("Data Entry Error - customer first name contains invalid characters.")
        else:
            break

    allowed_cust_last_name_char = set("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz-.,'")
    while True:
        CustLastName = input("Enter the customers last name: ").title()

        if CustLastName == "":
            print("Data Entry Error - customer last name cannot be blank.")
        elif set(CustLastName).issubset(allowed_cust_last_name_char) == False:
            print("Data Entry Error - customer last name contains invalid characters.")
        else:
            break


    allowed_st_add_char = set("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz-.,'1234567890")
    while True:
        StAdd = input("Enter the customers adress: ")

        if StAdd == "":
            print("Data Entry Error - customer adress cannot be blank.")
        elif set(StAdd).issubset(allowed_st_add_char) == False:
            print("Data Entry Error - customer adress contains invalid characters.")
        else:
            break

    allowed_city_char = set("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz-.,'")
    while True:
        City = input("Enter the customers city: ").title()

        if City == "":
            print("Data Entry Error - customer city cannot be blank.")
        elif set(City).issubset(allowed_city_char) == False:
            print("Data Entry Error - customer city contains invalid characters.")
        else:
            break

    ProvLst = ["NL", "NS", "NB", "PE", "PQ", "ON", "MB", "AB", "BC", "NT", "YT", "NV"]
    while True:
        Prov = input("Enter the customer province or territory (LL): ")
        
        if Prov == "":
            print("Error - cannot be blank.")
        elif len(Prov) != 2:
            print("Error - Must be 2 characters only.")
        elif Prov not in ProvLst:
            print("Error - invalid province or territory.")
        else:
            break

    allowed_postal_code_char =("ABCDEFGHIJKLMNOPQRSTUVWXZY 1234567890")
    while True:
        PostalCode = input("Enter the customers postal code (L9L 9L9): ")

        if PostalCode == "":
            print("Data Entry Error - customer postal code cannot be blank.")
        elif set(PostalCode).issubset(allowed_postal_code_char) == False:
            print("Data Entry Error - customer postal code contains invalid characters.")
        else:
            break

    while True:

        try:
            NumCarsIns = input("Enter the number of cars being insured: ")
            NumCarsIns = int(NumCarsIns)
        except:
            print("Data Entry Error - number of cars being insured is not a valid number.")
        else:
            if NumCarsIns == "":
                print("Data Entry Error - number of cars being insured cannot be blank.")
            else:
                break

    while True:
        ExtraLibility = input("Enter if the customer wants Extra Libility (Y/N): ").upper()

        if ExtraLibility == "":
            print("Data Entry Error - Extra Libility cannot be blank.")
        elif ExtraLibility != "Y" and ExtraLibility != "N":
            print("Data Entry Error - Extra Libility must be either Y or N.")
        else:
            break

    
    while True:
        GlassCoverage = input("Enter if the customer wants Glass Coverage (Y/N): ").upper()

        if GlassCoverage == "":
            print("Data Entry Error - Glass Coverage cannot be blank.")
        elif GlassCoverage != "Y" and GlassCoverage != "N":
            print("Data Entry Error - Glass Coverage must be either Y or N.")
        else:
            break

    while True:
        LoanerCar = input("Enter if the customer wants a loaner car (Y/N): ").upper()

        if LoanerCar == "":
            print("Data Entry Error - loaner car cannot be blank.")
        elif LoanerCar != "Y" and LoanerCar != "N":
            print("Data Entry Error - loaner car must be either Y or N.")
        else:
            break

    PaymentLst = ["Full", "Monthly", "Down Payment"]
    DownPaymentAmt = 0
    
    PaymentMethod = input("Enter the customer payment method (Full, Monthly, Down Payment): ")

    if PaymentMethod == "Down Payment":
            DownPaymentAmt = input("Enter the down payment amount: ")
            DownPaymentAmt = float(DownPaymentAmt)
    
    
            
    CustomerClaims()

    #Perform required calculations
    if NumCarsIns == 1:
        InsurPremium = BASIC_PREM
    elif NumCarsIns > 1:
        InsurPremium = BASIC_PREM * ADD_CAR_DIS

    ExtraLibilityCost = 0
    if ExtraLibility == "Y":
        ExtraLibilityCost = EXTRA_LIBILITY_COV
    
    GlassCoverageCost = 0
    if GlassCoverage == "Y":
        GlassCoverageCost = GLASS_COV
    
    LoanerCarCost = 0
    if LoanerCar == "Y":
        LoanerCarCost = LOAN_CAR_RATE

    TotExtraCost = ExtraLibilityCost + GlassCoverageCost + LoanerCarCost

    TotInsurPremium = BASIC_PREM + TotExtraCost

    HST = TotInsurPremium * HST_RATE

    TotalCost = TotInsurPremium + HST

    if PaymentMethod == "Down Payment":
        MonthlyPayment = (TotalCost - DownPaymentAmt) + PROCESSING_FEE / 8
    else:
        MonthlyPayment = (PROCESSING_FEE + TotalCost) / 8
    
    

    # Display Results 
    print()
    print(f" ONE STOP INSURANCE COMPANY")
    print(f" INSURANCE POLICY RECEIPT")                                 
    print(" -----------------------------------------")        
    print(f" Customer first name:                 {CustFirstName:<10s}")
    print(f" Customer last name:              {CustLastName:<10s}")
    print(f" Street adress:   {StAdd:<25s}")
    print(f" City:                          {City:<15s}")
    print(f" Province:                              {Prov:<2s}")
    print(f" Postal code:                       {PostalCode:<7s}")
    print(" -----------------------------------------")
    print(f" # of cars insured:                     {NumCarsIns:>2d}")
    print(f" Extra libility:                         {ExtraLibility:<1s}")
    print(f" Glass coverage:                         {GlassCoverage:<1s}")
    print(f" Loaner car:                             {LoanerCar:<1s}")
    print(" -----------------------------------------")
    print(f" Payment method:              {PaymentMethod:>12s}")
    
    if PaymentMethod == "Down Payment":
        print(f" Down payment amount:            {FV.FDollar2(DownPaymentAmt):>9s}")
    
    print(f" Total insurance premium:        {FV.FDollar2(TotInsurPremium):>9s}")
    print(f" Extra libility cost:            {FV.FDollar2(ExtraLibilityCost):>9s}")
    print(f" Glass coverage cost:            {FV.FDollar2(GlassCoverageCost):>9s}")
    print(f" Loaner car cost:                {FV.FDollar2(LoanerCarCost):>9s}")
    print(" -----------------------------------------")
    print(f" Total extra cost:               {FV.FDollar2(TotExtraCost):>9s}")
    print(f" HST:                            {FV.FDollar2(HST):>9s}")
    print(f" Total cost:                     {FV.FDollar2(TotalCost):>9s}")
    print(" -----------------------------------------")
    if PaymentMethod == "Monthly" or PaymentMethod == "Down Payment":
        print(f" Monthly payment                 {FV.FDollar2(MonthlyPayment):>9s}")
    print()
    print(f" Invoice date:                  {FV.FDateS(CURR_DATE):<10s}")
   
    if PaymentMethod == "Down Payment"  or PaymentMethod == "Monthly":
        TODAYPlus30 = CURR_DATE + datetime.timedelta(days = 30)
        TodayPlus30Dsp =datetime.datetime.strftime(TODAYPlus30, "%Y-%m-%d")
        print(f" First payment date:            {TodayPlus30Dsp}")
    
    print(" -----------------------------------------")
    print(f" Claim #  Claim Date                Amount")
    for i in range(len(ClaimNumLst)):
        print(f" {ClaimNumLst[i]:<4d}    {FV.FDateSQAP4(ClaimDateLst[i]):>10s}            {FV.FDollar2(ClaimAmtLst[i]):>10s}")

    
    print()

    # Store data in claims.dat

    for _ in range(5):  # Change to control no. of 'blinks'
        print('Saving claim data ...', end='\r')
        time.sleep(.3)  # To create the blinking effect
        sys.stdout.write('\033[2K\r')  # Clears the entire line and carriage returns
        time.sleep(.3)

    f = open("Claims.dat", "a")
    
    f.write("{}, ".format(str(CURR_DATE)))
    f.write("{}, ".format(StAdd)) 
    CustName = CustFirstName + " " + CustLastName
    f.write("{}, ".format(CustName)) 
    f.write("{}, ".format(City)) 
    f.write("{}, ".format(Prov)) 
    f.write("{}, ".format(PostalCode)) 
    f.write("{}, ".format(str(NumCarsIns)))
    f.write("{}\n".format(ExtraLibility))
    f.write("{}\n".format(GlassCoverage))
    f.write("{}\n".format(LoanerCar)) 
    f.write("{}\n".format(PaymentMethod))
    f.write("{}\n".format(str(DownPaymentAmt)))
    f.write("{}\n".format(str(InsurPremium)))     
    f.write("{}\n".format(str(TotInsurPremium))) 

    f.close()

    print()
    
    print()
    print("Claim data successfully saved ...", end='\r')
    time.sleep(1)  # To create the blinking effect
    sys.stdout.write('\033[2K\r')  # Clears the entire line and carriage returns

    POLICY_NUM += 1

    while True:
        Continue = input("Would you like to process another insurance policy? (Y/N): ")
        if Continue != "Y" and Continue != "N":
            print("Data Entry Error - Must enter either Y or N.")
        else:
            break
    if Continue == "N":
        break


# Housekeeping

f = open('Def.dat', 'w')
f.write("{}\n".format(str(POLICY_NUM)))
f.write("{}\n".format(str(BASIC_PREM)))
f.write("{}\n".format(str(ADD_CAR_DIS)))
f.write("{}\n".format(str(EXTRA_LIBILITY_COV)))
f.write("{}\n".format(str(GLASS_COV)))
f.write("{}\n".format(str(LOAN_CAR_RATE)))
f.write("{}\n".format(str(HST_RATE)))
f.write("{}\n".format(str(PROCESSING_FEE)))
f.close()

print()

print("Thanks for using the One Stop Insurance insurance policy program!")
