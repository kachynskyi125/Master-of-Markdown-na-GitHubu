# Návod na přežití vývojáře: Jak zkrotit starý kód
*Vítejte v zóně, kde káva teče proudem a nikdo netuší, co ten kód vlastně dělá.* Každý programátor se dříve či později setká s projektem, který napsal někdo jiný před lety (nebo nedej bože vy sami včera). Panika v takové chvíli ničemu nepomůže. ~~Přece to ale hned nevzdáme!~~ Tato příručka vás provede základními kroky, jak nezbláznit se a kód úspěšně refaktorovat.

## 1. Fáze mapování terénu
Než se pustíte do jakýchkoliv úprav, musíte zjistit, s čím vlastně máte tu čest.

### První kroky po otevření projektu
- Prozkoumejte adresářovou strukturu repozitáře.
- Podívejte se do souboru `README.md` (pokud vůbec existuje).
- Raději **nic nemažte**, dokud přesně nevíte, co to dělá.

### Můj denní úkolovník
- [x] Vytvořit zálohu projektu
- [x] Zkontrolovat závislosti a verze balíčků
- [ ] Napsat chybějící testy
- [ ] Doufat, že to nespadne v produkci

## 2. Užitečné nástroje a dokumentace
Při práci se starým kódem se snadno ocitnete ztraceni bez správné dokumentace. Určitě se podívejte do [oficiální dokumentace Gitu](https://git-scm.com/doc), kde najdete záchranu, když se vám podaří rozbít historii větví, nebo navštivte [Stack Overflow](https://stackoverflow.com) pro řešení specifických chyb.

> Zlaté pravidlo programátora: Pokud to funguje, tak na to raději nesahejte.

## 3. Ukázka kódu pro nouzovou situaci
Někdy potřebujete rychle ověřit, zda server vůbec žije. Zde je jednoduchý a užitečný skript v Pythonu, který vás zachrání:

```python
import http.client

def check_server(host):
    conn = http.client.HTTPConnection(host, timeout=5)
    try:
        conn.request("HEAD", "/")
        response = conn.getresponse()
        print(f"Server {host} žije! Status: {response.status}")
    except Exception as e:
        print(f"Chyba připojení: {e}")

if __name__ == "__main__":
    check_server("localhost")
```
    
## 4. Porovnání přístupů k refaktoringu
Následující tabulka porovnává dvě hlavní strategie při údržbě staršího softwaru:
Strategie | Výhody | Nevýhody | 
| :--- | :---: | :---: |            
**Inkrementální úpravy** | Menší riziko výpadku, průběžné testování | Trvá to delší dobu
**Kompletní rewrite** | Čistý kód, moderní technologie | Často se protáhne a vyrobí nové chyby

### Vizualizace pracovní reality
Následující obrázek přesně vystihuje moment, kdy se snažíte pochopit logiku cizího kódu bez komentářů:
A nezapomeňte – každý bug je jen skrytá featura!
