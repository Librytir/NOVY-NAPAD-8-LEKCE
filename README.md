# NOVY-NAPAD-8-LEKCE

Dobrý den, posílám Vám dodělanou lekci 8.
    Inspiroval jsem se jinými nápady na internetu od jiných uživatelů.

# Importujeme knihovny:
# random - pro náhodný výběr částí příšerky
# time - abychom mohli použít time.sleep() pro pauzy
import random
import time

# Funkce pro vytvoření náhodné příšerky
def vytvor_priseru():
    # Každý seznam obsahuje různé varianty části těla
    # Používáme seznamy, protože z nich můžeme jednoduše vybírat náhodně

    hlavy = ["(°□°)", "(ಠ_ಠ)", "(ᵔᴥᵔ)", "(☉_☉)"]
    tela = ["|###|", "|ooo|", "|===|", "|+++|"]
    nohy = ["/   \\", "/|||\\", "/^^^\\", "/---\\"]

    # random.choice vybere náhodný prvek ze seznamu
    hlava = random.choice(hlavy)
    telo = random.choice(tela)
    nohy_cast = random.choice(nohy)

    # Vrátíme celou příšerku jako seznam řádků
    return [hlava, telo, nohy_cast]


# Funkce pro dramatické vykreslení
def vykresli_priseru(prisera):
    print("Vyvolávám příšerku", end="", flush=True)

    # Smyčka for se používá, protože chceme opakovat akci několikrát
    for _ in range(3):
        time.sleep(0.7)  # pauza pro napětí
        print(".", end="", flush=True)

    print("\n")

    # Postupně vypisujeme jednotlivé části příšerky
    # Díky tomu vznikne efekt „postupného odhalení“
    for cast in prisera:
        time.sleep(1)  # pauza mezi částmi
        print(cast)


# Hlavní část programu
def main():
    # Podmínka není nutná, ale funkce main zlepšuje přehlednost kódu
    prisera = vytvor_priseru()
    vykresli_priseru(prisera)

    # Nabídneme uživateli opakování
    while True:
        odpoved = input("\nChceš další příšerku? (ano/ne): ").lower()

        # Podmínka kontroluje vstup uživatele
        # Používáme ji, abychom mohli program ukončit nebo zopakovat
        if odpoved == "ano":
            prisera = vytvor_priseru()
            vykresli_priseru(prisera)
        elif odpoved == "ne":
            print("Tak zase někdy 👻")
            break  # break ukončí cyklus while
        else:
            print("Zadej prosím 'ano' nebo 'ne'.")


# Tato podmínka zajistí, že se main() spustí jen při přímém spuštění souboru
if __name__ == "__main__":
    main()

