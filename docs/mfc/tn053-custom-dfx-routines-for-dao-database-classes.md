---
title: 'TN053: Niestandardowe procedury DFX dla DAO bazy danych klasy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dfx
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47d1c9769055e0ab69f57f58b136b7844cb1f860
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: niestandardowe procedury DFX dla klas baz danych DAO
> [!NOTE]
>  Środowiska Visual C++ i kreatorów nie obsługują DAO (mimo że uwzględniono klasy DAO i nadal można ich używać). Firma Microsoft zaleca użycie [szablony OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiekty DAO należy używać tylko w zachowaniu istniejących aplikacji.  
  
 Ta uwaga techniczna opisuje mechanizm wymiany (DFX) pól rekordów DAO. Aby lepiej poznać działania wykonywane w procedury DFX `DFX_Text` funkcji zostanie szczegółowo opisane w przykładzie. Jako dodatkowe źródło informacji do tej uwagi techniczne można zbadać kod dla siebie poszczególne funkcje DFX. Prawdopodobnie nie będzie konieczne niestandardowe procedury DFX tyle razy, ile trzeba niestandardowe procedury RFX (używany z klasami baz danych ODBC).  
  
 Ta uwaga techniczna zawiera:  
  
-   Omówienie DFX  
  
- [Przykłady](#_mfcnotes_tn053_examples) przy użyciu wymiana pól rekordów DAO i wiązania dynamicznego  
  
- [Jak działa DFX](#_mfcnotes_tn053_how_dfx_works)  
  
- [Co to jest Twoje procedury DFX niestandardowych](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
- [Dfx_text — szczegóły](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **Omówienie DFX**  
  
 Mechanizm wymiany pól rekordów DAO (DFX) jest używane w celu uproszczenia procedury pobierania i aktualizowania danych, korzystając z `CDaoRecordset` klasy. Upraszcza proces przy użyciu elementów członkowskich danych `CDaoRecordset` klasy. Przez pochodny `CDaoRecordset`, elementy członkowskie danych można dodać do klasy pochodnej reprezentujący każdego pola w tabeli lub zapytaniu. Ten mechanizm "wiązanie statyczne" jest proste, ale może nie być metodę pobierania lub zaktualizowania danych wyboru dla wszystkich aplikacji. DFX pobiera co pole powiązane zawsze, gdy zostanie zmieniona bieżącego rekordu. Jeśli tworzysz aplikację wrażliwych wydajności, która nie wymaga pobieranie każdego pola po zmianie waluty "wiązania dynamicznego" za pośrednictwem `CDaoRecordset::GetFieldValue` i `CDaoRecordset::SetFieldValue` może być wybranej metody dostępu.  
  
> [!NOTE]
>  DFX i wiązania dynamicznego nie są wykluczają się wzajemnie, dzięki hybrydowego stosowania statycznych i dynamicznych powiązania mogą być używane.  
  
## <a name="_mfcnotes_tn053_examples"></a> Przykład 1 — Użycie tylko wymiana pól rekordów DAO  
  
 (przyjęto założenie, `CDaoRecordset` — pochodnej klasy `CMySet` już otwarty)  
  
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
  
 **Przykład 3 — Użyj elementu DAO wymiana pól rekordów i wiązania dynamicznego**  
  
 (przyjęto założenie, przeglądania danych pracowników z `CDaoRecordset`-klasy `emp`)  
  
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
  
 Mechanizm DFX działa w sposób podobny do pól rekordów mechanizmu programu exchange (RFX) używane przez MFC ODBC — klasy. Zasady DFX i RFX są takie same, ale różnią się wiele wewnętrznych. Funkcje DFX projektu był taki, że prawie cały kod jest współużytkowany przez poszczególne procedury DFX. W tylko najwyższego poziomu DFX ma kilka rzeczy.  
  
-   DFX tworzy SQL **wybierz** klauzuli i SQL **parametry** klauzuli w razie potrzeby.  
  
-   DFX tworzy struktury powiązania, używany przez jego DAO `GetRows` funkcji (więcej informacji na ten temat poniżej).  
  
-   DFX zarządza buforu danych używaną do wykrywania pól z zanieczyszczeniu (jeśli jest używane podwójnego buforowania)  
  
-   Zarządza DFX **NULL** i **DIRTY** stan stałych i w razie potrzeby ustawia wartości na aktualizacje.  
  
 Istotą DFX jest mechanizm `CDaoRecordset` w klasie pochodnej `DoFieldExchange` funkcji. Ta funkcja wysyła wywołania poszczególnych funkcji DFX typu odpowiednie działania. Przed wywołaniem `DoFieldExchange` funkcje MFC wewnętrznej Ustaw typ operacji. Na poniższej liście przedstawiono różne typy operacji i krótki opis.  
  
|Operacja|Opis|  
|---------------|-----------------|  
|**AddToParameterList**|Klauzula parametry kompilacji|  
|**AddToSelectList**|Klauzula SELECT kompilacji|  
|**BindField**|Konfiguruje powiązanie — struktura|  
|**BindParam**|Ustawia wartości parametrów|  
|**Naprawy**|Ustawia stan o wartości NULL|  
|**AllocCache**|Przydziela pamięć podręczna dla wyboru z zanieczyszczeniu|  
|**StoreField**|Zapisuje bieżący rekord w pamięci podręcznej|  
|**LoadField**|Przywraca pamięci podręcznej, aby wartości elementów członkowskich|  
|**FreeCache**|Zwalnia pamięć podręczna|  
|`SetFieldNull`|Ustawia pola wartość NULL & stanu|  
|**MarkForAddNew**|Znaki pól zanieczyszczone, jeśli nie PSEUDO NULL|  
|**MarkForEdit**|Jeśli zanieczyszczone pola Znaczniki nie zgadzają się pamięci podręcznej|  
|**SetDirtyField**|Ustawia pole wartości oznaczony jako zmieniony|  
  
 W następnej sekcji opisano każdej operacji bardziej szczegółowo dla `DFX_Text`.  
  
 Informacje o procesie wymiany pól rekordów DAO najważniejszych funkcji jest używanych `GetRows` funkcji `CDaoRecordset` obiektu. Obiekt DAO `GetRows` funkcja może działać na kilka sposobów. Ta uwaga techniczna krótko opisano `GetRows` ponieważ jest poza zakresem tej uwagi techniczne.  
  
 Obiekty DAO `GetRows` można pracować na kilka sposobów.  
  
-   Go można pobrać wiele rekordów i używanie wielu pól danych w tym samym czasie. Dzięki temu dla szybszy dostęp do danych z complication postępowania z struktury dużej ilości danych i odpowiednie przesunięcia do każdego pola i dla każdego rekordu danych w strukturze. MFC nie korzystać z tego rekordu wielu mechanizmu pobierania.  
  
-   Innym sposobem `GetRows` można pracy jest umożliwienie deweloperom określić adres powiązanie dla każdego pola w jednym rekordzie danych pobrane dane.  
  
-   Obiekty DAO będzie również "wywołania zwrotnego" do wywołującego dla kolumn o zmiennej długości w celu umożliwienia obiekt wywołujący, aby przydzielić pamięci. Ta funkcja drugi ma korzyści, minimalizując liczbę kopii danych, a także zezwalanie bezpośredniego magazynu danych do elementów członkowskich klasy ( `CDaoRecordset` klasy). Ten mechanizm drugi jest metoda MFC używa do powiązania elementów członkowskich danych w `CDaoRecordset` klas pochodnych.  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> Co to jest Twoje procedury DFX niestandardowych  
 Jest widoczna od rozważania najważniejszych operacji w dowolnej funkcji DFX musi być umożliwia konfigurowanie struktury danych wymagane do pomyślnego wywołania `GetRows`. Liczba innych operacji, które funkcja DFX muszą również obsługiwać, ale nie jako ważne lub złożonych jako poprawnie przygotowania do `GetRows` wywołania.  
  
 Użycie DFX opisano w dokumentacji online. Zasadniczo istnieją dwa wymagania. Najpierw należy dodać członków do `CDaoRecordset` klasy dla każdego pola i parametru. Czynności opisane w tym `CDaoRecordset::DoFieldExchange` powinna zostać zastąpiona. Należy pamiętać, że typ danych elementu członkowskiego. Należy go pasują do danych z pola w bazie danych lub co najmniej możliwa do przekonwertowania na tego typu. Na przykład pola numerycznego w bazie danych, takich jak długich liczb całkowitych zawsze można przekonwertować na tekst i powiązane z `CString` — członek, ale pole tekstowe w bazie danych może nie musi to być przekonwertować do reprezentacji liczbowej, takich jak długich liczb całkowitych i powiązany z integ długi Era elementu członkowskiego. DAO i aparatu bazy danych programu Microsoft Jet są zobowiązani do konwersji (zamiast MFC).  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Dfx_text — szczegóły  
 Jak wspomniano wcześniej, najlepszy sposób, aby wyjaśnić, jak działa DFX jest do pracy z przykładem. W tym celu przechodzenia przez funkcje wewnętrzne `DFX_Text` powinny działać bardzo dobrze, aby zapewnić co najmniej podstawową wiedzę DFX.  
  
 **AddToParameterList**  
 Ta operacja Kompilacje SQL **parametry** klauzuli ("`Parameters <param name>, <param type> ... ;`") wymagane przez Jet. Każdy parametr jest o nazwie i wpisana (określone w wywołaniu RFX). Zobacz opis funkcji **CDaoFieldExchange::AppendParamType** funkcji, aby wyświetlić nazwy poszczególnych typów. W przypadku liczby `DFX_Text`, jest używany typ `text`.  
  
 **AddToSelectList**  
 Kompilacje SQL **wybierz** klauzuli. Jest to bardzo proste do przodu jako nazwa kolumny określona przez wywołanie DFX jest po prostu dołączany ("`SELECT <column name>, ...`").  
  
 **BindField**  
 Najbardziej złożonych operacji. Jak wspomniano wcześniej, jest to, gdzie DAO struktury powiązanie używane przez `GetRows` jest skonfigurowany. Jak widać z kodu w `DFX_Text` typy informacji w strukturze użytej DAO (**DAO_CHAR** lub **DAO_WCHAR** w odniesieniu `DFX_Text`). Dodatkowo typ powiązania używanego jest również ustawić. W sekcji wcześniejszych `GetRows` został krótko opisano, ale jest wystarczające, aby wyjaśnić, typ powiązania używanego przez MFC jest zawsze powiązanie bezpośredniego adresu (**DAOBINDING_DIRECT**). Ponadto dla powiązania kolumny o zmiennej długości (takie jak `DFX_Text`) powiązania wywołania zwrotnego jest używana co MFC można kontrolować alokacji pamięci i określić adres właściwą długość. Co to oznacza to, że MFC zawsze stwierdzić DAO ", gdzie" umieszczanie danych, dzięki czemu powiązanie bezpośrednio do zmiennych Członkowskich. Reszty struktury powiązanie jest wypełniane np. adres funkcja wywołania zwrotnego alokacji pamięci i typ powiązania kolumny (powiązanie według nazwy kolumn).  
  
 **BindParam**  
 To jest prostą operacją wywołującą `SetParamValue` z wartością parametru określony w elemencie członkowskim z parametru.  
  
 **Naprawy**  
 Wypełnia **NULL** stanu dla każdego pola.  
  
 `SetFieldNull`  
 Ta operacja oznacza tylko stan każdego pola jako **NULL** i ustawia wartość zmiennej członka **PSEUDO_NULL**.  
  
 **SetDirtyField**  
 Wywołania `SetFieldValue` dla każdego pola oznaczonych jako zakłócone.  
  
 Wszystkie pozostałe operacje dotyczą tylko przy użyciu pamięci podręcznej danych. Pamięć podręczna danych jest dodatkowy bufor danych bieżącego rekordu, który używa w celu uproszczenia pewne zagadnienia. Na przykład pola "zakłóconych" może być wykrywane automatycznie. Zgodnie z opisem w dokumentacji online go można wyłączyć całkowicie lub na poziomie pola. Implementacja buforu wykorzystuje mapy. Ta mapa jest używany do dopasowywania się dynamicznie przydzielonego kopie danych z adresem pole "powiązane" (lub `CDaoRecordset` pochodnego elementu członkowskiego danych).  
  
 **AllocCache**  
 Dynamicznie przydziela wartość pola pamięci podręcznej i dodaje go do mapy.  
  
 **FreeCache**  
 Usuwa wartość pola pamięci podręcznej i usuwa go z mapy.  
  
 **StoreField**  
 Kopiuje bieżącą wartość pola do pamięci podręcznej danych.  
  
 **LoadField**  
 Kopiuje wartość w pamięci podręcznej do elementu członkowskiego pola.  
  
 **MarkForAddNew**  
 Sprawdza, czy bieżąca wartość pola ma wartość inną niż**NULL** i oznacza je zanieczyszczony w razie potrzeby.  
  
 **MarkForEdit**  
 Porównuje bieżącą wartość pola z pamięci podręcznej danych i oznacza zanieczyszczone, jeśli to konieczne.  
  
> [!TIP]
>  Model Twoje niestandardowe procedury DFX na istniejące procedury DFX dla typów danych standardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

