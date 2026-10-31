# Personal SIM Manager - Apna Record
# Ye code kisi aur ka data nahi nikalta, sirf jo aap khud add karenge wohi dikhayega

sims_database = {}

def sim_add_karen():
    cnic = input("Apna CNIC (bina dash ke) daalein: ")
    name = input("Apna Naam daalein: ")
    sim_number = input("SIM Number daalein: ")
    network = input("Network (Jazz, Zong, etc): ")

    if cnic not in sims_database:
        sims_database[cnic] = {"name": name, "sims": []}
    
    sims_database[cnic]["sims"].append({"number": sim_number, "network": network})
    print(f"\nSIM {sim_number} save ho gayi!\n")

def sim_check_karen():
    cnic = input("\nApna CNIC daalein jiski SIMs dekhni hain: ")
    if cnic in sims_database:
        data = sims_database[cnic]
        print(f"\n--- CNIC: {cnic} ---")
        print(f"Name: {data['name']}")
        print("SIMs:")
        for sim in data['sims']:
            print(f"  - {sim['number']} ({sim['network']})")
    else:
        print("\nIs CNIC ka koi record nahi mila. Pehle SIM add karen.")
        print("Official check ke liye 668 par SMS karen ya cnic.sims.pk visit karen.")

# Program start
while True:
    print("\n1. Apni SIM Add Karen")
    print("2. Apni SIMs Dekhein (CNIC se)")
    print("3. Exit")
    choice = input("Option choose karen: ")

    if choice == '1':
        sim_add_karen()
    elif choice == '2':
        sim_check_karen()
    elif choice == '3':
        break
