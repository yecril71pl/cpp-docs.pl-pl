---
title: 'TN043: RFX Routines'
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 18820c7d17ddea355490ee32679d5d690ec3533e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294489"
---
# <a name="tn043-rfx-routines"></a>TN043: RFX Routines

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisano architekturę programu exchange (RFX) pola rekordów. Ponadto opisano, jak pisać **RFX_** procedury.

## <a name="overview-of-record-field-exchange"></a>Omówienie wymiana pól rekordów

Wszystkie funkcje pól rekordów są wykonywane przy użyciu kodu w języku C++. Nie istnieją żadne specjalne zasoby ani magic makra. Serce mechanizmu jest funkcja wirtualna, która musi zostać zastąpiona w każdej klasie pochodnej zestawu rekordów. Zawsze znajduje się w tym formularzu:

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

Komentarze AFX specjalny format umożliwiają ClassWizard zlokalizować i edytować kod w ramach tej funkcji. Kod, który nie jest zgodny z ClassWizard powinna znajdować się poza komentarze specjalny format.

W powyższym przykładzie \<recordset_exchange_field_type_call > ma postać:

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

i \<recordset_exchange_function_call > ma postać:

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

Większość **RFX_** funkcje mają trzy argumenty, jak pokazano powyżej, ale niektóre (np. `RFX_Text` i `RFX_Binary`) mają dodatkowe argumenty opcjonalne.

Więcej niż jeden **RFX_** mogą być zawarte w każdej `DoDataExchange` funkcji.

Zobacz "afxdb.h", aby uzyskać listę wszystkich rekordów pola procedury wymiany dostarczane z MFC.

Zestaw rekordów pola wywołania są sposób rejestrowania lokalizacji pamięci (zazwyczaj elementy członkowskie danych) do przechowywania danych pola dla `CMySet` klasy.

## <a name="notes"></a>Uwagi

Funkcje pól rekordów zostały zaprojektowane do pracy tylko w przypadku `CRecordset` klasy. Nie są one zazwyczaj mogą być używane przez innych klas MFC.

Początkowe wartości danych są ustawiane w Konstruktorze standard C++, zazwyczaj w bloku z `//{{AFX_FIELD_INIT(CMylSet)` i `//}}AFX_FIELD_INIT` komentarzy.

Każdy **RFX_** funkcję musi obsługiwać różne operacje, od zwracanie stanu zanieczyszczone tego pola do archiwizacji pola w ramach przygotowania do edytowania pola.

Każda funkcja, która wywołuje `DoFieldExchange` (na przykład `SetFieldNull`, `IsFieldDirty`), jest inicjacji wokół wywołania `DoFieldExchange`.

## <a name="how-does-it-work"></a>Jak to działa

Nie musisz zrozumieć następujące czynności, aby można było używać wymiana pól rekordów. Jednak zrozumienie, jak to działa w tle pomoże Ci napisać własnej procedury wymiany.

`DoFieldExchange` Funkcja członkowska jest podobne do `Serialize` funkcji składowej — odpowiada za pobieranie lub ustawianie danych do i z postaci zewnętrznych (w tym przypadków kolumnach z wynikiem zapytania ODBC) od i do dane elementu członkowskiego w klasie. *PFX* parametr kontekstu do wykonywania wymiany danych i jest podobna do *CArchive* parametr `CObject::Serialize`. *PFX* ( `CFieldExchange` obiekt) ma wskaźnik operacji, która jest podobna do, ale uogólnieniem *CArchive* Flaga kierunku. Funkcja RFX może być konieczne obsługuje następujące operacje:

- `BindParam` — Wskazuje, gdzie ODBC należy pobrać dane parametru

- `BindFieldToColumn` — Wskazać, gdzie ODBC musi pobrać/depozytu outputColumn danych

- `Fixup` — Ustaw `CString/CByteArray` długości, Ustaw stan o wartości NULL, bit

- `MarkForAddNew` — Mark zakłóconych, jeśli wartość została zmieniona, ponieważ działają funkcje AddNew wywołania

- `MarkForUpdate` — Mark zakłóconych, jeśli wartość została zmieniona od czasu wywołania edycji

- `Name` — Dołącz nazwy pól dla pól oznaczona jako zanieczyszczona

- `NameValue` — Dołącz "\<nazwa kolumny > =" oznaczona jako zanieczyszczona pól

- `Value` — Dołącz "" następuje separatora, takie jak "," lub ""

- `SetFieldDirty` — Ustaw pole (czyli zmienione) zanieczyszczeniu bit stanu

- `SetFieldNull` — Ustawia bit stan wskazujący wartość null dla pola

- `IsFieldDirty` — Zwraca wartość stanu zanieczyszczeniu bit

- `IsFieldNull` — Zwraca wartość bitowa status o wartości null

- `IsFieldNullable` — Zwraca wartość TRUE, jeśli pole może zawierać wartości NULL

- `StoreField` — Wartość pola archiwum

- `LoadField` — Załaduj ponownie zarchiwizowane wartość pola

- `GetFieldInfoValue` — Zwraca informacje ogólne na pole

- `GetFieldInfoOrdinal` — Zwraca informacje ogólne na pole

## <a name="user-extensions"></a>Rozszerzenia dla użytkowników

Istnieje kilka sposobów, aby rozszerzyć domyślnego mechanizmu RFX. Można

- Dodaj nowe typy danych. Na przykład:

    ```cpp
    CBookmark
    ```

- Dodaj nowe procedury wymiany (RFX_).

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- Masz `DoFieldExchange` funkcja elementu członkowskiego warunkowe obejmują dodatkowe wywołania RFX lub inne prawidłowe instrukcje języka C++.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> Taki kod nie może być przez nich edytowane ClassWizard i powinny być używane wyłącznie poza komentarze specjalny format.

## <a name="writing-a-custom-rfx"></a>Pisanie niestandardowych RFX

Aby napisać własną funkcję RFX niestandardowe, zaleca się skopiowanie istniejącej funkcji RFX i modyfikować go odpowiednio do własnych celów. Wybieranie RFX prawo, aby skopiować może ułatwić zadania znacznie. Niektóre funkcje RFX mają unikalne właściwości, które należy wziąć pod uwagę przy podejmowaniu decyzji, który można skopiować.

`RFX_Long` i `RFX_Int`: Są to najprostsza funkcje RFX. Wartość danych nie wymaga żadnych specjalnych interpretacji i rozmiaru danych jest stały.

`RFX_Single` i `RFX_Double`: Podobnie jak rfx_long — i rfx_int — powyżej, te funkcje są proste i ułatwia korzystanie z domyślną implementację często. Są one przechowywane w dbflt.cpp zamiast dbrfx.cpp, jednak aby umożliwić ładowanie środowiska uruchomieniowego liczb zmiennoprzecinkowych biblioteki punktu, tylko wtedy, gdy są one jawnie odwołania.

`RFX_Text` i `RFX_Binary`: Te dwie funkcje przydzielenia statycznego bufor do przechowywania informacji ciąg/dane binarne i należy zarejestrować bufory Procedura SQLBindCol ODBC zamiast wartości & rejestrowanie. W związku z tym te dwie funkcje mają wiele szczególny kodu.

`RFX_Date`: ODBC zwraca informacje daty i godziny w ich własnych TIMESTAMP_STRUCT strukturę danych. Ta funkcja przydziela dynamicznie TIMESTAMP_STRUCT jako "proxy" do wysyłania i odbierania danych czasowych daty. Informacje o datę i godzinę dla różnych operacji musi być przenoszony między C++ `CTime` obiektu i TIMESTAMP_STRUCT serwera proxy. To znacznie komplikuje tej funkcji, ale jest dobrym przykładem przedstawiającym sposób użycia serwera proxy do transferu danych.

`RFX_LongBinary`: Jest to tylko Biblioteka klasy funkcji RFX, która nie używa powiązanie kolumny w celu odbierania i wysyłania danych. Ta funkcja ignoruje operacji BindFieldToColumn zamiast tego podczas operacji naprawy, przydziela magazynu do przechowywania danych przychodzących SQL_LONGVARCHAR lub SQL_LONGVARBINARY, a następnie wykonuje wywołanie Procedura SQLGetData do pobrania wartości do przydzielenia pamięci. Podczas przygotowywania do wysłania wartości danych z powrotem do źródła danych (na przykład operacje wartości nazwy i wartości), ta funkcja korzysta z funkcji DATA_AT_EXEC ODBC firmy. Zobacz [techniczne 45 Uwaga](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) Aby uzyskać więcej informacji na temat pracy z SQL_LONGVARBINARY i SQL_LONGVARCHARs.

Podczas pisania własnych **RFX_** funkcji, często można używać `CFieldExchange::Default` do wykonania danej operacji. Przyjrzyj się z implementacji domyślnej dla danego działania. Jeśli go wykonuje operację będzie można pisania w swojej **RFX_** funkcji, możesz delegować `CFieldExchange::Default`. Zawiera przykłady wywoływania `CFieldExchange::Default` w dbrfx.cpp

Ważne jest, aby wywołać `IsFieldType` na początku funkcji RFX i zwrócenia natychmiast, jeśli zwraca wartość FALSE. Ten mechanizm przechowuje parametr operacje wykonywane na *outputColumns*i na odwrót (takich jak wywoływanie `BindParam` na *outputColumn*). Ponadto `IsFieldType` automatycznie śledzi informacje o łącznej liczby *outputColumns* (*m_nfields —*) i parametry (*m_nparams —*).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
