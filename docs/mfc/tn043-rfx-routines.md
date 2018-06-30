---
title: 'TN043: Procedury RFX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RFX
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0c53ed2d1f1ab1a965a913287c8b5c171903518
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122773"
---
# <a name="tn043-rfx-routines"></a>TN043: procedury RFX

> [!NOTE]
> Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.

Ta uwaga opis architektury pól rekordów (RFX) programu exchange. Opisano również sposób zapisu **RFX_** procedury.

## <a name="overview-of-record-field-exchange"></a>Omówienie wymiana pól rekordów

Kod w języku C++ są wykonywane wszystkie funkcje pól rekordów. Nie ma żadnych specjalnych zasobów lub magic makra. Mechanizm to wirtualnego funkcję, która musi zostać zastąpiona w każdej klasy pochodnej zestawu rekordów. Zawsze znajduje się w tym formularzu:

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

Komentarze AFX specjalny format Zezwalaj ClassWizard do lokalizowania i edytować kod w tej funkcji. Kod, który nie jest zgodny z ClassWizard powinny być umieszczone poza komentarze specjalny format.

W powyższym przykładzie < recordset_exchange_field_type_call > ma postać:

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

i < recordset_exchange_function_call > ma postać:

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

Większość **RFX_** funkcji ma trzy argumenty, jak pokazano powyżej, ale niektóre (np. `RFX_Text` i `RFX_Binary`) ma dodatkowe argumenty opcjonalne.

Więcej niż jeden **RFX_** może być zawarta w każdym `DoDataExchange` funkcji.

Zobacz "afxdb.h", aby uzyskać listę wszystkich rekordów pola procedury wymiany podaną w MFC.

Zestaw rekordów wywołania pola są sposób rejestrowania lokalizacji pamięci (zazwyczaj elementy członkowskie danych) do przechowywania danych pola dla `CMySet` klasy.

## <a name="notes"></a>Uwagi

Funkcje pól rekordów są zaprojektowane do pracy tylko z `CRecordset` klasy. Nie są one zazwyczaj mogą być używane przez innych klas MFC.

Wartości początkowe dane są ustawione w Konstruktorze standard C++, zazwyczaj w bloku z `//{{AFX_FIELD_INIT(CMylSet)` i `//}}AFX_FIELD_INIT` komentarze.

Każdy **RFX_** funkcja musi obsługiwać różne operacje, od powrotu stanu zanieczyszczone pola do archiwizacji pola w ramach przygotowania do edycji pole.

Każda funkcja, która wywołuje `DoFieldExchange` (na przykład `SetFieldNull`, `IsFieldDirty`), jest inicjowania wokół wywołanie `DoFieldExchange`.

## <a name="how-does-it-work"></a>Jak to działa

Nie trzeba zrozumieć następujące, aby można było używać wymiana pól rekordów. Jednak zrozumienia, jak to działa w tle zawierają informacje pomocne podczas zapisu procedura programu exchange.

`DoFieldExchange` Funkcja członkowska jest podobne jak w przypadku `Serialize` funkcji członkowskiej — jest odpowiedzialny za pobierania lub ustawiania danych do/z formularza zewnętrznych (w tym wielkość kolumnach wyniku kwerendy ODBC) od i do elementu członkowskiego danych w klasie. *PFX* parametr kontekstu dla podczas wymiany danych i jest podobny do *CArchive* parametr `CObject::Serialize`. *PFX* ( `CFieldExchange` obiektu) zawiera wskaźnik operacja, która jest podobna do, ale generalizacji z *CArchive* Flaga kierunku. Funkcja RFX może być konieczne obsługuje następujące operacje:

- `BindParam` — Wskazuje, gdzie ODBC należy pobrać danych parametru

- `BindFieldToColumn` — Wskazuje gdzie ODBC musi pobrać/depozytu outputColumn danych

- `Fixup` — Wartość `CString/CByteArray` długości, Ustaw stan NULL bit

- `MarkForAddNew` — Znacznik zmieniony, jeśli wartość została zmieniona od wywołania metody AddNew

- `MarkForUpdate` — Znacznik zmieniony, jeśli wartość zmienił się od czasu wywołania edycji

- `Name` — Dołącz nazwy pól dla pól oznaczonych jako zakłócone

- `NameValue` — Append "\<nazwa kolumny > =" dla pól oznaczonych jako zakłócone

- `Value` — Append "" następuje separatora, takich jak ',' lub ' "

- `SetFieldDirty` — Ustaw stan bit zanieczyszczone pola (tj. zmienione)

- `SetFieldNull` — Ustawia bit stan wskazujący wartość null dla pola

- `IsFieldDirty` — Zwracana wartość stanu zanieczyszczone bitowe

- `IsFieldNull` — Zwracanej wartości bitowe stan o wartości null

- `IsFieldNullable` — Zwraca wartość TRUE, jeśli pole może zawierać wartości NULL

- `StoreField` — Wartość pola archiwum

- `LoadField` — Wartość pola zarchiwizowane Załaduj ponownie

- `GetFieldInfoValue` — Zwracają informacje ogólne dla pola

- `GetFieldInfoOrdinal` — Zwracają informacje ogólne dla pola

## <a name="user-extensions"></a>Rozszerzenia użytkownika

Istnieje kilka sposobów, aby rozszerzyć domyślny mechanizm RFX. Można

- Dodaj nowe typy danych. Na przykład:

    ```cpp
    CBookmark
    ```

- Dodaj nowe procedury programu exchange (RFX_).

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- Ma `DoFieldExchange` funkcji członkowskiej warunkowo obejmują dodatkowe RFX wywołań lub innych prawidłowy instrukcji C++.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> Taki kod nie może być edytowany przez ClassWizard i powinna być używana tylko poza komentarze specjalny format.

## <a name="writing-a-custom-rfx"></a>Pisanie niestandardowych RFX

Aby napisać funkcji RFX niestandardowe, zaleca się skopiowanie istniejącej funkcji RFX i zmodyfikuj go do własnych celów. Wybieranie RFX prawo, aby skopiować może ułatwić zadanie znacznie. Niektóre funkcje RFX mają niektóre unikatowe właściwości, które należy wziąć pod uwagę podczas wybierania który do skopiowania.

`RFX_Long` i `RFX_Int`: są to najprostsza funkcji RFX. Wartość danych nie wymaga żadnych specjalnych interpretacji, a rozmiar danych jest stała.

`RFX_Single` i `RFX_Double`: rfx_long — podobnie jak rfx_int — powyżej, te funkcje są proste i ułatwia użycie Domyślna implementacja często. Są one przechowywane w dbflt.cpp zamiast dbrfx.cpp, jednak aby włączyć ładowanie środowiska uruchomieniowego zmiennoprzecinkową biblioteki punktu tylko wtedy, gdy są one jawnie odwołania.

`RFX_Text` i `RFX_Binary`: te dwie funkcje przydzielenia statycznych buforu do przechowywania informacji o ciągu/dwuargumentowy i zarejestrować bufory z ODBC Procedura SQLBindCol zamiast wartości & rejestrowania. W związku z tym te dwie funkcje mają wiele specjalny przypadek kodu.

`RFX_Date`: ODBC zwraca informacje o datę i godzinę w ich własnych TIMESTAMP_STRUCT struktury danych. Ta funkcja dynamicznie przydziela TIMESTAMP_STRUCT jako "proxy" do wysyłania i odbierania danych czasu daty. Informacji daty i godziny dla różnych operacji musi być przenoszony między C++ `CTime` obiekt i TIMESTAMP_STRUCT serwera proxy. To znacznie komplikuje tej funkcji, ale jest dobrym przykładem przedstawiającym sposób użycia serwera proxy do transferu danych.

`RFX_LongBinary`: To jest tylko biblioteki klas funkcji RFX, które nie są używane powiązanie kolumny do odbierania i wysyłania danych. Ta funkcja ignoruje operacji BindFieldToColumn zamiast tego podczas operacji naprawy przydzielania magazynu do przechowywania danych przychodzących SQL_LONGVARCHAR lub SQL_LONGVARBINARY, a następnie wykonuje wywołanie Procedura SQLGetData do pobierania wartości do Magazyn przydzielony. Podczas przygotowywania do wysyłania danych z powrotem do źródła danych (takich jak nazwa i wartość operacji), ta funkcja używa funkcji DATA_AT_EXEC ODBC firmy. Zobacz [45 Uwaga techniczna](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) Aby uzyskać więcej informacji na temat pracy z SQL_LONGVARBINARY i SQL_LONGVARCHARs.

Podczas zapisywania własnych **RFX_** funkcji, często można używać `CFieldExchange::Default` implementacji danej operacji. Szukaj w implementacji domyślnej dla danej operacji. Jeśli wykonuje operację będzie można pisanie w Twojej **RFX_** funkcji można delegować do `CFieldExchange::Default`. Zawiera przykłady wywołania metody `CFieldExchange::Default` w dbrfx.cpp

Ważne jest, aby wywołać `IsFieldType` na początku tej funkcji RFX i wróć natychmiast, jeśli zwraca wartość FALSE. Ten mechanizm przechowuje parametru operacji wykonywane w *outputColumns*i na odwrót (takie jak wywołania `BindParam` na *outputColumn*). Ponadto `IsFieldType` automatycznie przechowuje informacje o liczbę *outputColumns* (*m_nfields —*) i parametry (*m_nparams —*).

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  
