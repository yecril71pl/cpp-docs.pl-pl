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
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365261"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: niestandardowe procedury DFX dla klas baz danych DAO

> [!NOTE]
> DAO jest używany z bazami danych programu Access i jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą. Środowisko Visual C++ i kreatory nie obsługują DAO (chociaż klasy DAO są uwzględniane i nadal można ich używać). Firma Microsoft zaleca używanie [szablonów ole db](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Dao należy używać tylko w utrzymaniu istniejących aplikacji.

Niniejsza uwaga techniczna opisuje mechanizm wymiany pól rekordów DAO (DFX). Aby pomóc zrozumieć, co dzieje się w `DFX_Text` procedurach DFX, funkcja zostanie szczegółowo wyjaśniona jako przykład. Jako dodatkowe źródło informacji do tej uwagi technicznej, można sprawdzić kod dla innych poszczególnych funkcji DFX. Prawdopodobnie nie będzie potrzebny niestandardowy DFX rutynowych tak często, jak może być potrzebne niestandardowe procedury RFX (używane z klasami bazy danych ODBC).

Niniejsza uwaga techniczna zawiera:

- Przegląd DFX

- [Przykłady](#_mfcnotes_tn053_examples) użycia wymiany pól rekordów DAO i powiązania dynamicznego

- [Jak działa DFX](#_mfcnotes_tn053_how_dfx_works)

- [Co robi niestandardowa procedura DFX](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Szczegóły DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Przegląd DFX**

Mechanizm wymiany pól rekordu DAO (DFX) służy do uproszczenia procedury `CDaoRecordset` pobierania i aktualizowania danych podczas korzystania z klasy. Proces jest uproszczony przy użyciu `CDaoRecordset` elementów członkowskich danych klasy. Wyprowadzając z `CDaoRecordset`programu , można dodać elementy członkowskie danych do klasy pochodnej reprezentującej każde pole w tabeli lub kwerendzie. Ten mechanizm "wiązania statycznego" jest prosty, ale może nie być metodą pobierania/aktualizacji danych dla wszystkich aplikacji. DFX pobiera każde pole powiązane za każdym razem, gdy bieżący rekord zostanie zmieniony. Jeśli tworzysz aplikację zależną od wydajności, która nie wymaga pobierania każdego pola po `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` zmianie waluty, "wiązanie dynamiczne" za pośrednictwem i może być metodą dostępu do danych z wyboru.

> [!NOTE]
> DFX i wiązanie dynamiczne nie wykluczają się wzajemnie, więc można użyć hybrydowego użycia wiązania statycznego i dynamicznego.

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>Przykład 1 — Użycie tylko wymiany pól rekordu DAO

(zakłada `CDaoRecordset` , klasa `CMySet` pochodna już otwarta)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Przykład 2 — Użycie tylko wiązania dynamicznego**

(zakłada, `CDaoRecordset` że `rs`przy użyciu klasy, i jest już otwarty)

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

**Przykład 3 — Użycie wymiany pól rekordów DAO i powiązania dynamicznego**

(zakłada przeglądanie danych `CDaoRecordset`pracowników z `emp`klasą pochodną )

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

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>Jak działa DFX

Mechanizm DFX działa w podobny sposób do mechanizmu wymiany pól rekordów (RFX) używanego przez klasy OdBC MFC. Zasady DFX i RFX są takie same, ale istnieją liczne różnice wewnętrzne. Konstrukcja funkcji DFX była taka, że praktycznie cały kod jest współużytkowany przez poszczególne procedury DFX. Na najwyższym poziomie DFX robi tylko kilka rzeczy.

- DFX konstruuje klauzulę SQL **SELECT** i klauzulę **SQL PARAMETERS,** jeśli to konieczne.

- DFX konstruuje strukturę wiązania używaną przez `GetRows` funkcję DAO (więcej na ten temat później).

- DFX zarządza buforem danych używanym do wykrywania brudnych pól (jeśli używane jest podwójne buforowanie)

- DFX zarządza tablicami stanu **NULL** i **DIRTY** i ustawia wartości w razie potrzeby w aktualizacjach.

Sercem mechanizmu DFX jest `CDaoRecordset` funkcja klasy pochodnej. `DoFieldExchange` Ta funkcja wywołuje wywołania do poszczególnych funkcji DFX odpowiedniego typu operacji. Przed `DoFieldExchange` wywołaniem wewnętrznych funkcji MFC ustawić typ operacji. Na poniższej liście przedstawiono różne typy operacji i krótki opis.

|Operacja|Opis|
|---------------|-----------------|
|`AddToParameterList`|Tworzy klauzulę PARAMETRY|
|`AddToSelectList`|Tworzy klauzulę SELECT|
|`BindField`|Konfiguruje strukturę wiązania|
|`BindParam`|Ustawia wartości parametrów|
|`Fixup`|Ustawia stan NULL|
|`AllocCache`|Przydziela pamięć podręczną do brudnego sprawdzania|
|`StoreField`|Zapisuje bieżący rekord w pamięci podręcznej|
|`LoadField`|Przywraca pamięć podręczną do wartości członkowskich|
|`FreeCache`|Zwalnia pamięć podręczną|
|`SetFieldNull`|Ustawia wartość & stanu pola na WARTOŚĆ NULL|
|`MarkForAddNew`|Oznacza pola zabrudzone, jeśli nie PSEUDO NULL|
|`MarkForEdit`|Oznacza pola zabrudzone, jeśli nie pasują do pamięci podręcznej|
|`SetDirtyField`|Ustawia wartości pól oznaczone jako zabrudzone|

W następnej sekcji każda operacja zostanie wyjaśniona `DFX_Text`bardziej szczegółowo dla .

Najważniejszą funkcją, aby zrozumieć o procesie wymiany pola rekordu `GetRows` DAO `CDaoRecordset` jest to, że używa funkcji obiektu. Funkcja DAO `GetRows` może działać na kilka sposobów. Niniejsza uwaga techniczna będzie tylko krótko opisywać, `GetRows` ponieważ nie jest to objęte zakresem niniejszej noty technicznej.
DAO `GetRows` może działać na kilka sposobów.

- Może pobierać wiele rekordów i wiele pól danych w tym czasie. Pozwala to na szybszy dostęp do danych z komplikacją radzenia sobie z dużą strukturą danych i odpowiednie przesunięcia do każdego pola i dla każdego rekordu danych w strukturze. MFC nie korzysta z tego mechanizmu pobierania wielu rekordów.

- Innym `GetRows` sposobem może działać jest umożliwienie programistom określić adresy powiązania dla pobranych danych każdego pola dla jednego rekordu danych.

- DAO będzie również "oddzwonić" do obiektu wywołującego dla kolumn o zmiennej długości, aby umożliwić wywołującemu przydzielić pamięć. Ta druga funkcja ma tę zaletę, że minimalizuje liczbę kopii danych, a także umożliwia `CDaoRecordset` bezpośrednie przechowywanie danych do członków klasy (klasy pochodnej). Ten drugi mechanizm jest metoda MFC używa do `CDaoRecordset` powiązania z elementów członkowskich danych w klasach pochodnych.

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Co robi niestandardowa procedura DFX

Z tej dyskusji wynika, że najważniejszą operacją zaimplementowana w dowolnej funkcji DFX musi `GetRows`być możliwość skonfigurowania wymaganych struktur danych, aby pomyślnie wywołać . Istnieje wiele innych operacji, które funkcja DFX musi obsługiwać, jak również, ale `GetRows` żaden tak ważne lub złożone, jak poprawnie przygotowuje się do wywołania.

Korzystanie z DFX jest opisane w dokumentacji online. Zasadniczo istnieją dwa wymagania. Najpierw elementy członkowskie muszą `CDaoRecordset` zostać dodane do klasy pochodnej dla każdego powiązanego pola i parametru. Następnie `CDaoRecordset::DoFieldExchange` należy zastąpić. Należy zauważyć, że typ danych elementu członkowskiego jest ważne. Powinien być zgodny z danymi z pola w bazie danych lub przynajmniej być konwertowane do tego typu. Na przykład pole liczbowe w bazie danych, takie jak długa liczba całkowita, zawsze `CString` można przekonwertować na tekst i powiązać z elementem członkowskim, ale pole tekstowe w bazie danych niekoniecznie musi być konwertowane na reprezentację liczbową, taką jak długa liczba całkowita i powiązaną z długim elementem członkowskim liczby całkowitej. DAO i aparat bazy danych Microsoft Jet są odpowiedzialne za konwersję (a nie MFC).

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>Szczegóły DFX_Text

Jak wspomniano wcześniej, najlepszym sposobem wyjaśnienia, jak działa DFX, jest praca przez przykład. W tym celu przechodząc przez `DFX_Text` wewnętrzne powinny działać całkiem dobrze, aby pomóc zapewnić co najmniej podstawowe zrozumienie DFX.

- `AddToParameterList`

   Ta operacja tworzy klauzulę SQL`Parameters <param name>, <param type> ... ;` **PARAMETERS** (" ") wymaganą przez jet. Każdy parametr jest nazwany i wpisany (jak określono w wywołaniu RFX). Zobacz funkcję `CDaoFieldExchange::AppendParamType` funkcji, aby wyświetlić nazwy poszczególnych typów. W przypadku `DFX_Text`, używanym typem jest **tekst**.

- `AddToSelectList`

   Tworzy klauzulę SQL **SELECT.** Jest to dość proste, ponieważ nazwa kolumny określona przez wywołanie`SELECT <column name>, ...`DFX jest po prostu dołączana (" ").

- `BindField`

   Najbardziej złożonych operacji. Jak wspomniano wcześniej jest to, gdzie struktura `GetRows` wiązania DAO używane przez jest skonfigurowany. Jak widać z kodu `DFX_Text` w typach informacji w strukturze obejmują typ DAO używane (**DAO_CHAR** lub `DFX_Text` **DAO_WCHAR** w przypadku ). Ponadto typ wiązania używane jest również skonfigurowany. We wcześniejszej `GetRows` sekcji opisano tylko krótko, ale wystarczyło wyjaśnić, że rodzaj wiązania używanego przez MFC jest zawsze bezpośrednim powiązaniem adresów (**DAOBINDING_DIRECT**). Ponadto dla powiązania kolumny o `DFX_Text`zmiennej długości (jak) wiązania wywołania zwrotnego jest używany tak, że MFC można kontrolować alokacji pamięci i określić adres o poprawnej długości. Oznacza to, że MFC zawsze można powiedzieć DAO "gdzie", aby umieścić dane, umożliwiając w ten sposób powiązanie bezpośrednio do zmiennych członkowskich. Pozostała część struktury powiązania jest wypełniona rzeczy, takie jak adres funkcji wywołania zwrotnego alokacji pamięci i typ powiązania kolumny (powiązanie według nazwy kolumny).

- `BindParam`

   Jest to prosta operacja, która wywołuje `SetParamValue` z wartością parametru określoną w elementów członkowskich parametru.

- `Fixup`

   Wypełnia stan **NULL** dla każdego pola.

- `SetFieldNull`

   Ta operacja oznacza tylko każdy stan pola jako **NULL** i ustawia wartość zmiennej elementu członkowskiego na **PSEUDO_NULL**.

- `SetDirtyField`

   Wywołania `SetFieldValue` dla każdego pola oznaczonego jako zabrudzone.

Wszystkie pozostałe operacje dotyczą tylko przy użyciu pamięci podręcznej danych. Pamięć podręczna danych jest dodatkowym buforem danych w bieżącym rekordzie, który jest używany do uproszczenie pewnych rzeczy. Na przykład pola "brudne" mogą być wykrywane automatycznie. Jak opisano w dokumentacji online, można go wyłączyć całkowicie lub na poziomie pola. Implementacja buforu wykorzystuje mapę. Ta mapa służy do dopasowywać dynamicznie przydzielone kopie danych z adresem `CDaoRecordset` pola "powiązanego" (lub pochodnego elementu członkowskiego danych).

- `AllocCache`

   Dynamicznie przydziela wartość pola w pamięci podręcznej i dodaje ją do mapy.

- `FreeCache`

   Usuwa wartość pola w pamięci podręcznej i usuwa ją z mapy.

- `StoreField`

   Kopiuje bieżącą wartość pola do pamięci podręcznej danych.

- `LoadField`

   Kopiuje wartość buforowaną do elementu członkowskiego pola.

- `MarkForAddNew`

   Sprawdza, czy bieżąca wartość pola nie jest**NULL** i oznacza ją zabrudzone, jeśli to konieczne.

- `MarkForEdit`

   Porównuje bieżącą wartość pola z pamięcią podręczną danych i w razie potrzeby oznacza zabrudzenie.

> [!TIP]
> Modelowanie niestandardowych procedur DFX na istniejących procedurach DFX dla standardowych typów danych.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
