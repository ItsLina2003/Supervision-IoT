from pymodbus.client import ModbusTcpClient

# Adresse IP et port du S7-1200
PLC_IP = "192.168.1.10"  # Remplace par l'IP de ton automate
PLC_PORT = 502  # Port Modbus TCP

# Connexion au S7-1200
client = ModbusTcpClient(PLC_IP, port=PLC_PORT)

if client.connect():
    print("Connexion réussie à l'automate S7-1200")

    # LIRE des registres (exemple : lire la température du registre 40001)
    registre = 0  # Adresse Modbus (40001 -> 0 en base 0)
    lecture = client.read_holding_registers(registre, 1)  # Lire 1 registre

    if not lecture.isError():
        print(f"Valeur lue du registre {registre + 40001} : {lecture.registers[0]}")
    else:
        print("Erreur de lecture")

    # ÉCRIRE dans un registre (exemple : activer une pompe sur le registre 40002)
    registre_ecriture = 1  # Adresse Modbus (40002 -> 1 en base 0)
    valeur = 1  # 1 = Activer la pompe, 0 = Désactiver
    ecriture = client.write_register(registre_ecriture, valeur)

    if not ecriture.isError():
        print(f"Valeur {valeur} écrite dans le registre {registre_ecriture + 40001}")
    else:
        print("Erreur d'écriture")

    # Fermer la connexion
    client.close()
else:
    print("Échec de connexion au S7-1200")
from pymodbus.client import ModbusTcpClient

# Adresse IP et port du S7-1200
PLC_IP = "192.168.1.10"  # Remplace par l'IP de ton automate
PLC_PORT = 502  # Port Modbus TCP

# Connexion au S7-1200
client = ModbusTcpClient(PLC_IP, port=PLC_PORT)

if client.connect():
    print("Connexion réussie à l'automate S7-1200")

    # LIRE des registres (exemple : lire la température du registre 40001)
    registre = 0  # Adresse Modbus (40001 -> 0 en base 0)
    lecture = client.read_holding_registers(registre, 1)  # Lire 1 registre

    if not lecture.isError():
        print(f"Valeur lue du registre {registre + 40001} : {lecture.registers[0]}")
    else:
        print("Erreur de lecture")

    # ÉCRIRE dans un registre (exemple : activer une pompe sur le registre 40002)
    registre_ecriture = 1  # Adresse Modbus (40002 -> 1 en base 0)
    valeur = 1  # 1 = Activer la pompe, 0 = Désactiver
    ecriture = client.write_register(registre_ecriture, valeur)

    if not ecriture.isError():
        print(f"Valeur {valeur} écrite dans le registre {registre_ecriture + 40001}")
    else:
        print("Erreur d'écriture")

    # Fermer la connexion
    client.close()
else:
    print("Échec de connexion au S7-1200")
