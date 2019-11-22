---
title: 'TN053: niestandardowe procedury DFX dla klas baz danych DAO'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: 6dde96520d9472726da86f8da295770cccc5d42c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303436"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: niestandardowe procedury DFX dla klas baz danych DAO

> [!NOTE]
>  Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały. Środowisko i C++ kreatory wizualne nie obsługują obiektów DAO (mimo że klasy DAO są dołączone i nadal można ich używać). Firma Microsoft zaleca korzystanie z [szablonów OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC oraz MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiektów DAO należy używać tylko w przypadku zarządzania istniejącymi aplikacjami.

Ta Uwaga techniczna zawiera opis mechanizmu wymiany pól rekordów DAO (DFX). Aby pomóc zrozumieć, co dzieje się w procedurach DFX, funkcja `DFX_Text` zostanie szczegółowo omówiona jako przykład. Jako dodatkowe źródło informacji na temat tej uwagi technicznej można przeanalizować kod dla innych funkcji DFX. Prawdopodobnie nie będzie potrzebna niestandardowa procedura DFX, tak często, jak może być wymagana niestandardowa procedura RFX (używana z klasami baz danych ODBC).

Ta Uwaga techniczna zawiera następujące kwestie:

- DFX — Omówienie

- [Przykłady](#_mfcnotes_tn053_examples) używające wymiany pól rekordów DAO i powiązania dynamicznego

- [Jak działa DFX](#_mfcnotes_tn053_how_dfx_works)

- [Co to jest niestandardowa procedura DFX](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Szczegóły DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**DFX — Omówienie**

Mechanizm wymiany pól rekordów DAO (DFX) służy do uproszczenia procedury pobierania i aktualizowania danych przy użyciu klasy `CDaoRecordset`. Proces jest uproszczony przy użyciu składowych danych klasy `CDaoRecordset`. Dzięki wykorzystaniu z `CDaoRecordset`można dodać składowe danych do klasy pochodnej reprezentującej każde pole w tabeli lub kwerendzie. Mechanizm "powiązania statycznego" jest prosty, ale może nie być to metoda pobierania/aktualizowania danych dla wszystkich aplikacji. DFX pobiera każde pole powiązane za każdym razem, gdy bieżący rekord został zmieniony. W przypadku tworzenia aplikacji z uwzględnieniem wydajności, która nie wymaga pobierania każdego pola po zmianie waluty, "powiązanie dynamiczne" za pośrednictwem `CDaoRecordset::GetFieldValue` i `CDaoRecordset::SetFieldValue` może być metodą dostępu do danych.

> [!NOTE]
>  DFX i powiązanie dynamiczne nie wykluczają się wzajemnie, więc można używać hybrydowego powiązania statycznego i dynamicznego.

## <a name="_mfcnotes_tn053_examples"></a>Przykład 1 — Używanie tylko wymiany pól rekordów DAO

(zakłada `CDaoRecordset` — Klasa pochodna `CMySet` już otwarta)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Przykład 2 — Używanie tylko dynamicznego powiązania**

(przyjmuje się, że jest używana Klasa `CDaoRecordset`, `rs`i jest już otwarta)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**Przykład 3 — użycie wymiany pól rekordów DAO i powiązania dynamicznego**

(zakłada przeglądanie danych pracownika przy użyciu klasy pochodnej `CDaoRecordset``emp`)

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="_mfcnotes_tn053_how_dfx_works"></a>Jak działa DFX

Mechanizm DFX działa podobnie do mechanizmu wymiany pól rekordów (RFX) używanego przez klasy MFC ODBC. Zasady DFX i RFX są takie same, ale istnieje wiele różnic wewnętrznych. Projekt funkcji DFX był taki, że praktycznie cały kod jest współużytkowany przez poszczególne procedury DFX. Na najwyższym poziomie DFX tylko kilka rzeczy.

- DFX konstruuje klauzulę **SELECT** języka SQL i klauzulę SQL **Parameters** w razie potrzeby.

- DFX konstruuje strukturę powiązania używaną przez funkcję `GetRows` DAO (więcej informacji na ten temat).

- DFX zarządza buforem danych używanym do wykrywania zanieczyszczonych pól (jeśli jest używane podwójne buforowanie)

- DFX zarządza tablicami stanu o **wartości null** i **zanieczyszczony** oraz ustawia wartości w razie potrzeby w przypadku aktualizacji.

Przy użyciu mechanizmu DFX jest funkcją `DoFieldExchange` klasy pochodnej `CDaoRecordset`. Ta funkcja wysyła wywołania do poszczególnych funkcji DFX w odpowiednim typie operacji. Przed wywołaniem `DoFieldExchange` wewnętrznych funkcji MFC Ustaw typ operacji. Na poniższej liście przedstawiono różne typy operacji i Krótki opis.

|Operacja|Opis|
|---------------|-----------------|
|`AddToParameterList`|Klauzula Build PARAMETERS|
|`AddToSelectList`|Kompilacja — klauzula SELECT|
|`BindField`|Konfiguruje strukturę powiązania|
|`BindParam`|Ustawia wartości parametrów|
|`Fixup`|Ustawia stan NULL|
|`AllocCache`|Przydziela pamięć podręczną dla kontroli zanieczyszczonej|
|`StoreField`|Zapisuje bieżący rekord w pamięci podręcznej|
|`LoadField`|Przywraca pamięć podręczną do wartości elementów członkowskich|
|`FreeCache`|Pamięć podręczna FreeS|
|`SetFieldNull`|Ustawia stan pola & wartość na NULL|
|`MarkForAddNew`|Oznacza pola jako zanieczyszczone, jeśli nie ma PSEUDO wartości NULL|
|`MarkForEdit`|Oznacza pola jako zanieczyszczone, jeśli nie pasuje do pamięci podręcznej|
|`SetDirtyField`|Ustawia wartości pól oznaczone jako zanieczyszczone|

W następnej sekcji każda operacja zostanie omówiona bardziej szczegółowo dla `DFX_Text`.

Najważniejszym elementem do zrozumienia procesu wymiany pól rekordów DAO jest użycie funkcji `GetRows` obiektu `CDaoRecordset`. Funkcja DAO `GetRows` może działać na kilka sposobów. Ta Uwaga techniczna będzie krótko opisać `GetRows`, ponieważ znajduje się poza zakresem tej uwagi technicznej.
`GetRows` DAO można obsłużyć na kilka sposobów.

- Może jednocześnie pobierać wiele rekordów i wiele pól danych. Pozwala to przyspieszyć dostęp do danych przy użyciu dużej struktury danych i odpowiednich przesunięć do poszczególnych pól oraz dla każdego rekordu danych w strukturze. MFC nie korzysta z tego mechanizmu pobierania rekordu wielokrotnego.

- Innym sposobem `GetRows` może być umożliwienie programistom określania adresów powiązań dla pobranych danych każdego pola dla jednego rekordu danych.

- Obiekty DAO również są wywoływane do obiektu wywołującego dla kolumn o zmiennej długości, aby umożliwić obiektowi wywołującemu przydzielenie pamięci. Ta druga funkcja umożliwia zminimalizowanie liczby kopii danych, a także umożliwienie bezpośredniego magazynowania danych do elementów członkowskich klasy (Klasa pochodna `CDaoRecordset`). Drugim mechanizmem jest metoda MFC stosowana do tworzenia powiązań z elementami członkowskimi danych w `CDaoRecordset` klasach pochodnych.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Co to jest niestandardowa procedura DFX

Oczywiste jest, że najważniejsze operacje zaimplementowane w dowolnej funkcji DFX muszą mieć możliwość skonfigurowania wymaganych struktur danych w celu pomyślnego wywołania `GetRows`. Istnieje wiele innych operacji, które funkcja DFX musi obsługiwać, ale nie jako ważne ani złożone jako prawidłowo przygotowywanie do wywołania `GetRows`.

Użycie DFX jest opisane w dokumentacji online. Zasadniczo istnieją dwa wymagania. Najpierw należy dodać elementy członkowskie do klasy pochodnej `CDaoRecordset` dla każdego powiązanego pola i parametru. Należy zastąpić ten `CDaoRecordset::DoFieldExchange`. Należy zauważyć, że typ danych składowej jest ważny. Powinien on pasować do danych z pola w bazie danych lub co najmniej do konwersji na ten typ. Na przykład pole liczbowe w bazie danych, takie jak Long Integer, można zawsze być konwertowane na tekst i powiązane z `CString` składową, ale pole tekstowe w bazie danych może niekoniecznie być konwertowane na reprezentację liczbową, taką jak Long integer i powiązana z elementem członkowskim Long Integer. Program DAO i aparat bazy danych Microsoft Jet są odpowiedzialne za konwersję (a nie MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>Szczegóły DFX_Text

Jak wspomniano wcześniej, najlepszym sposobem na wyjaśnienie, jak działa DFX, jest przechodzenie przez przykład. W tym celu przechodzenie przez wewnętrzne `DFX_Text` powinno być przydatne, aby zapewnić co najmniej podstawową wiedzę na temat DFX.

- `AddToParameterList`

   Ta operacja kompiluje klauzulę SQL **Parameters** ("`Parameters <param name>, <param type> ... ;`") wymaganą przez aparat Jet. Każdy parametr ma nazwę i wpisano (jak określono w wywołaniu RFX). Zobacz funkcję `CDaoFieldExchange::AppendParamType` funkcji, aby wyświetlić nazwy poszczególnych typów. W przypadku `DFX_Text`używany typ to **Text**.

- `AddToSelectList`

   Kompiluje klauzulę **SELECT** języka SQL. Jest to bardzo proste, ponieważ nazwa kolumny określona przez wywołanie DFX jest po prostu dołączana ("`SELECT <column name>, ...`").

- `BindField`

   Najbardziej złożone operacje. Jak wspomniano wcześniej, jest to miejsce, w którym jest skonfigurowana struktura powiązań DAO używana przez `GetRows`. Jak widać w kodzie w `DFX_Text` typy informacji w strukturze obejmują używany typ DAO (**DAO_CHAR** lub **DAO_WCHAR** w przypadku `DFX_Text`). Ponadto zostanie również skonfigurowany typ użytego powiązania. W wcześniejszej sekcji `GetRows` zostało opisane tylko krótko, ale było wystarczające, aby wyjaśnić, że typ powiązania używany przez MFC jest zawsze bezpośrednim powiązaniem adresu (**DAOBINDING_DIRECT**). Dodatkowo dla powiązania kolumn o zmiennej długości (takie jak `DFX_Text`) jest używane powiązanie wywołania zwrotnego, aby MFC mogły kontrolować alokację pamięci i określać adres o poprawnej długości. Oznacza to, że MFC może zawsze informować DAO "Where", aby umieścić dane, umożliwiając powiązanie bezpośrednio z zmiennymi składowymi. Pozostałe struktury powiązań są wypełniane przy użyciu takich elementów jak adres funkcji wywołania zwrotnego alokacji pamięci i typ powiązania kolumny (powiązanie według nazwy kolumny).

- `BindParam`

   Jest to prosta operacja, która wywołuje `SetParamValue` z wartością parametru określoną w elemencie członkowskim parametru.

- `Fixup`

   Wypełnia stan **null** dla każdego pola.

- `SetFieldNull`

   Ta operacja oznacza tylko każdy stan pola jako **wartość null** i ustawia wartość zmiennej składowej na **PSEUDO_NULL**.

- `SetDirtyField`

   Wywołuje `SetFieldValue` dla każdego pola oznaczonego jako zanieczyszczone.

Wszystkie pozostałe operacje dotyczą tylko korzystania z pamięci podręcznej danych. Pamięć podręczna danych to dodatkowy bufor danych w bieżącym rekordzie, który jest używany do uproszczenia niektórych rzeczy. Na przykład pola "Dirty" mogą być wykrywane automatycznie. Zgodnie z opisem w dokumentacji online można ją wyłączyć całkowicie lub na poziomie pola. Implementacja buforu wykorzystuje mapę. Ta mapa służy do dopasowywania dynamicznie przypisywanych kopii danych przy użyciu adresu pola "Bound" (lub `CDaoRecordset` pochodnego elementu członkowskiego danych).

- `AllocCache`

   Dynamicznie przydziela wartość pola w pamięci podręcznej i dodaje ją do mapy.

- `FreeCache`

   Usuwa buforowaną wartość pola i usuwa ją z mapy.

- `StoreField`

   Kopiuje bieżącą wartość pola do pamięci podręcznej danych.

- `LoadField`

   Kopiuje wartość z pamięci podręcznej do elementu członkowskiego pola.

- `MarkForAddNew`

   Sprawdza, czy bieżąca wartość pola jest inna niż**null** i oznacza, że jest zanieczyszczona w razie potrzeby.

- `MarkForEdit`

   Porównuje bieżącą wartość pola z pamięcią podręczną danych i oznacza, że w razie potrzeby są zanieczyszczone.

> [!TIP]
> Modeluj niestandardowe procedury DFX na istniejących procedurach DFX dla standardowych typów danych.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
