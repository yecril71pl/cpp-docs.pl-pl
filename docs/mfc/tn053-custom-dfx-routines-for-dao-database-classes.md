---
title: 'TN053: Niestandardowe procedury DFX dla klas baz danych DAO'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dfx
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
ms.openlocfilehash: b610604c1b7a68128dc9eb6fb5515225ed22b16e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282412"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Niestandardowe procedury DFX dla klas baz danych DAO

> [!NOTE]
>  Środowiska Visual C++ i kreatory nie obsługują DAO (mimo że uwzględniono klas DAO i nadal można użyć). Firma Microsoft zaleca się, że używasz [szablony OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. DAO należy używać tylko w zachowaniu istniejących aplikacji.

Ta uwaga techniczna opisuje mechanizm wymiany (DXF) pola rekordów DAO. Aby lepiej zrozumieć, co się dzieje w procedury DFX `DFX_Text` funkcji zostaną wyjaśnione w szczegółowy przykład. Jako dodatkowe źródło informacji o tym Uwaga techniczna można sprawdzić kod dla siebie poszczególne funkcje DFX. Prawdopodobnie nie będą potrzebne niestandardowe procedury DFX tak często, jak możesz potrzebować niestandardowe procedury RFX (używany z klasami bazy danych ODBC).

Ta uwaga techniczna zawiera:

- Omówienie DFX

- [Przykłady](#_mfcnotes_tn053_examples) przy użyciu wymiana pól rekordów DAO i wiązanie dynamiczne

- [Jak działa DFX](#_mfcnotes_tn053_how_dfx_works)

- [What Your Custom DFX Routine Does](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Dfx_text — szczegóły](#_mfcnotes_tn053_details_of_dfx_text)

**Omówienie DFX**

Mechanizm wymiany pól rekordów DAO (DXF) jest używany do uproszczenia procedury pobierania i aktualizowania danych, korzystając z `CDaoRecordset` klasy. Ten proces jest uproszczone, za pomocą elementów członkowskich danych `CDaoRecordset` klasy. Przez pochodząca od `CDaoRecordset`, możesz dodać elementy członkowskie danych do klasy pochodnej, reprezentujący każdego pola w tabeli lub zapytanie. Ten mechanizm "wiązanie statyczne" jest proste, ale może nie być metodę pobierania/aktualizowanie danych wybranego dla wszystkich aplikacji. DFX pobiera wszystkich powiązanych pól w każdym razem, gdy bieżący rekord zostanie zmieniony. Jeśli tworzysz aplikację wrażliwego na wydajność, która nie wymaga pobieranie każde pole, po zmianie waluty "wiązanie dynamiczne" za pośrednictwem `CDaoRecordset::GetFieldValue` i `CDaoRecordset::SetFieldValue` może być wybranej metody dostępu.

> [!NOTE]
>  DFX i wiązanie dynamiczne nie są wzajemnie się wykluczają, więc hybrydowego użytkowania powiązania statycznych i dynamicznych może służyć.

## <a name="_mfcnotes_tn053_examples"></a> Przykład 1 — Użycie tylko wymiana pól rekordów DAO

(przyjęto założenie, `CDaoRecordset` — Klasa pochodna `CMySet` już otwarty)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Przykład 2 — Użyj tylko dynamiczne powiązania**

(przyjęto założenie, za pomocą `CDaoRecordset` klasy `rs`, i jest on już otwarty)

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

**Przykład 3 — Korzystanie z DAO wymiana pól rekordów i wiązanie dynamiczne**

(przyjęto założenie, przeglądania danych pracowników z `CDaoRecordset`-klasy pochodnej `emp`)

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a> Jak działa DFX

Mechanizm DFX działa w sposób podobny do pól rekordów mechanizmu programu exchange (RFX) używane przez klasy MFC ODBC. Zasady DFX i RFX są takie same, ale różnią się wiele wewnętrznych. Projekt funkcje DFX był taki, że prawie cały kod jest współużytkowany przez poszczególne procedury DFX. Na tylko najwyższego poziomu DFX wykonuje kilka czynności.

- DFX konstrukcji SQL **wybierz** SQL i klauzuli **parametry** klauzuli, jeśli to konieczne.

- DFX tworzy strukturę powiązania, używany przez firmy DAO `GetRows` — funkcja (więcej informacji na ten temat poniżej).

- DFX zarządza bufor danych służącą do wykrywania zanieczyszczone pola (jeśli jest on używany podwójnego buforowania)

- Zarządza DFX **NULL** i **DIRTY** stan tablice i ustawia wartości w razie potrzeby aktualizacji.

Serce DFX mechanizm jest `CDaoRecordset` w klasie pochodnej `DoFieldExchange` funkcji. Ta funkcja wywołuje wywołania poszczególne funkcje DFX typu odpowiedniego działania. Przed wywołaniem `DoFieldExchange` wewnętrzne funkcje MFC Ustaw typ operacji. Na poniższej liście przedstawiono różne typy operacji i krótki opis.

|Operacja|Opis|
|---------------|-----------------|
|`AddToParameterList`|Klauzula parametry kompilacji|
|`AddToSelectList`|Klauzula SELECT kompilacji|
|`BindField`|Konfiguruje powiązanie struktury|
|`BindParam`|Ustawia wartości parametrów|
|`Fixup`|Ustawia stan o wartości NULL|
|`AllocCache`|Przydziela pamięć podręczną o zanieczyszczeniu wyboru|
|`StoreField`|Zapisuje bieżący rekord w pamięci podręcznej|
|`LoadField`|Odtwarzanie pamięci podręcznej, aby wartości elementów członkowskich|
|`FreeCache`|Zwalnia pamięć podręczna|
|`SetFieldNull`|Ustawia pole stanu & wartość null|
|`MarkForAddNew`|Oznacza pola o zanieczyszczeniu w przeciwnym razie PSEUDO o wartości NULL|
|`MarkForEdit`|Jeśli zanieczyszczone pola Znaczniki nie są zgodne pamięci podręcznej|
|`SetDirtyField`|Ustawia pole wartości oznaczony jako zanieczyszczony|

W następnej sekcji, każda operacja zostaną wyjaśnione bardziej szczegółowo dla `DFX_Text`.

Najważniejszych funkcji o procesu wymiany pól rekordów DAO jest, że używa on `GetRows` funkcji `CDaoRecordset` obiektu. Obiekt DAO `GetRows` funkcja może działać na kilka sposobów. Ta uwaga techniczna krótko opisano `GetRows` się poza zakresem tej uwagi techniczne.

DAO `GetRows` może pracować na kilka sposobów.

- Jego można pobrać rekordów wielu i wiele pól tych danych w tym samym czasie. Dzięki temu szybsze dostępu do danych za pomocą kompilacji związanych z struktury dużych ilości danych i odpowiednie przesunięcia do każdego pola, jak i dla każdego rekordu danych w strukturze. MFC nie korzystać z tego rekordu wielu pobieranie mechanizm.

- Innym sposobem `GetRows` można pracy jest umożliwienie deweloperom Określ adresy powiązania dla pobranych danych każdego pola dla jednego rekordu danych.

- DAO będzie również "wywołania zwrotnego" do obiektu wywołującego dla kolumn o zmiennej długości w celu umożliwienia obiekt wywołujący, aby przydzielić pamięć. Ta druga funkcja ma tę zaletę, minimalizując liczbę kopii danych, a także co bezpośredniego przechowywania danych do elementów członkowskich klasy ( `CDaoRecordset` klasy pochodnej). Ten mechanizm drugi jest metoda używa MFC, aby powiązać elementy członkowskie danych w `CDaoRecordset` klas pochodnych.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> What Your Custom DFX Routine Does

Jest on widoczny z tej dyskusji, który najważniejszych operacji zaimplementowane w dowolnej funkcji DFX musi być możliwość Konfigurowanie struktury danych wymagane do pomyślnego wywołania `GetRows`. Istnieje wiele innych operacji, które funkcja DFX muszą również obsługiwać, ale brak jako ważne lub złożonego, jak poprawnie przygotowania `GetRows` wywołania.

Użycie DFX jest opisany w dokumentacji online. Zasadniczo istnieją dwa wymagania. Najpierw należy dodać członków do `CDaoRecordset` klasy dla każdego pola i parametrów. Zgodnie z dokumentem `CDaoRecordset::DoFieldExchange` powinna zostać zastąpiona. Należy pamiętać, że typ danych elementu członkowskiego jest ważne. Powinien on pasują do danych z pola w bazie danych lub co najmniej być konwertowany do tego typu. Na przykład pole liczbowe w bazie danych, takie jak liczba całkowita typu long, zawsze możesz przekonwertować ją na tekst i powiązane z `CString` elementu członkowskiego, ale pole tekstowe w bazie danych może nie musi to być przekonwertować do reprezentacji liczbowej, takie jak liczba całkowita typu long i powiązane z długich integ ER elementu członkowskiego. DAO i aparatu bazy danych Microsoft Jet są odpowiedzialne za konwersji (zamiast MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Dfx_text — szczegóły

Jak wspomniano wcześniej, najlepszym sposobem, aby wyjaśnić, jak działa DFX jest trzymać się przykładowi. W tym celu przechodzenia przez funkcje wewnętrzne `DFX_Text` powinny działać bardzo dobrze, aby zapewnić co najmniej podstawową wiedzę na temat DFX.

- `AddToParameterList`

   Ta operacja tworzy SQL **parametry** — klauzula ("`Parameters <param name>, <param type> ... ;`") wymaganego przez Jet. Każdego parametru jest nazwane i wpisane (określone w wywołaniu RFX). Zobacz opis funkcji `CDaoFieldExchange::AppendParamType` funkcji, aby wyświetlić nazwy poszczególnych typów. W przypadku właściwości `DFX_Text`, typ używany jest **tekstu**.

- `AddToSelectList`

   Kompilacje SQL **wybierz** klauzuli. Jest to całkiem proste jako nazwa kolumny określona przez wywołanie DFX jest po prostu dołączany ("`SELECT <column name>, ...`").

- `BindField`

   Najbardziej złożonych operacji. Jak wspomniano wcześniej, jest to, gdzie struktury powiązania DAO posługują się `GetRows` jest skonfigurowany. Jak widać w kodzie w `DFX_Text` typy informacji w strukturze obejmują typ DAO używany (**DAO_CHAR** lub **DAO_WCHAR** w przypadku właściwości `DFX_Text`). Ponadto typ powiązania używanego jest też skonfigurować. W wcześniejszej sekcji `GetRows` został krótko opisano go, ale wystarczające, aby wyjaśnić, typ powiązania używanego przez MFC jest zawsze powiązanie bezpośredniego adresu (**DAOBINDING_DIRECT**). Ponadto dla powiązania kolumny o zmiennej długości (takich jak `DFX_Text`) powiązania wywołania zwrotnego jest używany, aby kontrolować alokacji pamięci i określ adres odpowiednią długość MFC. Oznacza to, że MFC zawsze widnieć DAO "gdzie" mają umieszczać dane, dzięki czemu wiązanie bezpośrednio do zmiennych składowych. Pozostała część struktury powiązania jest wypełniane elementów, takich jak adres funkcji wywołania zwrotnego alokacji pamięci i typ powiązanie kolumny (powiązanie według nazwy kolumn).

- `BindParam`

   To jest prostą operacją, która wywołuje `SetParamValue` z wartością parametru określony w elemencie Członkowskim swoje parametru.

- `Fixup`

   Wypełnia **NULL** stanu dla każdego pola.

- `SetFieldNull`

   Ta operacja oznacza tylko stan każdego pola jako **NULL** i ustawia wartość zmiennej elementu członkowskiego na **PSEUDO_NULL**.

- `SetDirtyField`

   Wywołania `SetFieldValue` dla każdego pola, oznaczona jako zanieczyszczona.

Wszystkie pozostałe operacje zajmować się tylko przy użyciu pamięci podręcznej danych. Pamięć podręczna danych jest dodatkowy bufor danych w bieżącym rekordzie, który umożliwia pewne działania, prostsze. Na przykład pola "zakłóconych" może zostać automatycznie wykryte. Zgodnie z opisem w dokumentacji online go można wyłączyć całkowicie lub na poziomie pola. Implementacja buforu korzysta z mapy. Ta mapa jest używany do dopasowywania się dynamicznie przydzielonej kopii danych przy użyciu adresu pole "związane" (lub `CDaoRecordset` pochodzi element członkowski danych).

- `AllocCache`

   Dynamicznie przydziela wartość pola pamięci podręcznej i dodaje je do mapy.

- `FreeCache`

   Usuwa wartość pola pamięci podręcznej i usuwa go z mapy.

- `StoreField`

   Kopiuje bieżącą wartość pola do pamięci podręcznej danych.

- `LoadField`

   Kopiuje wartość w pamięci podręcznej do składowej pola.

- `MarkForAddNew`

   Sprawdza, czy bieżąca wartość pola non -**NULL** i oznacza je o zanieczyszczeniu w razie potrzeby.

- `MarkForEdit`

   Porównuje bieżącą wartość pola z pamięci podręcznej danych i oznaczy zanieczyszczony, jeśli to konieczne.

> [!TIP]
> Model swoje niestandardowe procedury DFX na istniejącej procedury DFX dla typów danych w warstwie standardowa.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
