# Documentație API - Geocode

## Introducere
Acest API permite obținerea coordonatelor geografice pe baza unei adrese furnizate. API-ul preia datele furnizate de utilizator și returnează rezultatele relevante utilizând informațiile din Google Maps.

---

## Endpoint

**URL:**  
`https://paulgabriel.dev/api/geocode.php`

**Metoda:**  
`GET`

---

## Parametri de intrare

API-ul acceptă mai mulți parametri, toți fiind opționali, dar cel puțin unul trebuie furnizat.

| Parametru   | Tip    | Obligatoriu | Descriere |
|------------|--------|-------------|-------------|
| `Judet`    | String | Nu | Județul unde se află adresa |
| `Localitate` | String | Nu | Localitatea unde se află adresa |
| `Strada`   | String | Nu | Strada din adresa căutată |
| `Nr`       | String | Nu | Numărul străzii |
| `Tara`     | String | Nu | Țara în care se află adresa |

---

## Exemple de utilizare

### Exemplu 1: Cerere minimală

```bash
curl -X GET "https://paulgabriel.dev/api/geocode.php?Judet=Bucuresti&Localitate=Bucuresti"
```

### Exemplu 2: Cerere completă

```bash
curl -X GET "https://paulgabriel.dev/api/geocode.php?Judet=Cluj&Localitate=Cluj-Napoca&Strada=Eroilor&Nr=10"
```

---

## Răspunsul API

Răspunsul API-ului este în format JSON și poate avea două tipuri de răspuns:

### Răspuns de succes
```json
{
    "error": false,
    "response": {
        "result": true,
        "postcode": "061088",
        "address": "Bl. 4P, 71, Bulevardul Iuliu Maniu, Militari, Sector 6, București, 061088, România",
        "bounds1": "[44.4333122,26.0133368]",
        "bounds2": "[44.4336753,26.0155893]",
        "lat": 44.43349084999999831779859960079193115234375,
        "lng": 26.014961820902268385680145001970231533050537109375
    }
}
```

### Răspuns de eroare
Dacă nu sunt furnizate suficiente date pentru a forma o adresă validă:
```json
{
    "error": true,
    "message": "Nu au fost furnizate informații suficiente pentru a construi adresa."
}
```

Dacă apare o eroare în procesarea cererii:
```json
{
    "error": true,
    "message": "Eroare la cerere: ..."
}
```

Dacă răspunsul primit este invalid:
```json
{
    "error": true,
    "message": "Răspuns JSON invalid sau răspuns gol primit."
}
```

---

## Observații
- API-ul permite accesul din orice domeniu (`Access-Control-Allow-Origin: *`), astfel încât poate fi utilizat în aplicații web.
- Datele sunt transmise prin `GET`, astfel încât trebuie URL-encode în cazul în care conțin caractere speciale.
- Înainte de a trimite cererea, adresa este preprocesată pentru a elimina caracterele speciale (ex. `ș` devine `s`, `ț` devine `t`, etc.).

---

## Contact
Pentru probleme sau sugestii, vă rugăm să contactați administratorul API-ului la: `contact@paulgabriel.dev`.

---

# API Documentation - Geocode

## Introduction
This API allows obtaining geographic coordinates based on a provided address. The API processes user-provided data and returns relevant results using information from Google Maps.

---

## Endpoint

**URL:**  
`https://paulgabriel.dev/api/geocode.php`

**Method:**  
`GET`

---

## Input Parameters

The API accepts multiple parameters, all optional, but at least one must be provided.

| Parameter   | Type  | Required | Description |
|------------|--------|-------------|-------------|
| `Judet`    | String | No | The county where the address is located |
| `Localitate` | String | No | The locality where the address is located |
| `Strada`   | String | No | The street of the searched address |
| `Nr`       | String | No | The street number |
| `Tara`     | String | No | The country where the address is located |

---

## Usage Examples

### Example 1: Minimal request

```bash
curl -X GET "https://paulgabriel.dev/api/geocode.php?Judet=Bucuresti&Localitate=Bucuresti"
```

### Example 2: Complete request

```bash
curl -X GET "https://paulgabriel.dev/api/geocode.php?Judet=Cluj&Localitate=Cluj-Napoca&Strada=Eroilor&Nr=10&Tara=Romania"
```

---

## API Response

The API response is in JSON format and can have two types:

### Success Response
```json
{
    "error": false,
    "response": {
        "result": true,
        "postcode": "061088",
        "address": "Bl. 4P, 71, Bulevardul Iuliu Maniu, Militari, Sector 6, București, 061088, România",
        "bounds1": "[44.4333122,26.0133368]",
        "bounds2": "[44.4336753,26.0155893]",
        "lat": 44.43349084999999831779859960079193115234375,
        "lng": 26.014961820902268385680145001970231533050537109375
    }
}
```

### Error Response
If insufficient data is provided to construct a valid address:
```json
{
    "error": true,
    "message": "Not enough information provided to construct the address."
}
```

If there is an error processing the request:
```json
{
    "error": true,
    "message": "Request error: ..."
}
```

If the received response is invalid:
```json
{
    "error": true,
    "message": "Invalid JSON response or empty response received."
}
```

---

## Notes
- The API allows access from any domain (`Access-Control-Allow-Origin: *`), making it suitable for web applications.
- Data is sent via `GET`, so special characters should be URL-encoded.
- Before sending the request, the address is preprocessed to remove special characters (e.g., `ș` becomes `s`, `ț` becomes `t`, etc.).

---

## Contact
For issues or suggestions, please contact the API administrator at: `contact@paulgabriel.dev`.
