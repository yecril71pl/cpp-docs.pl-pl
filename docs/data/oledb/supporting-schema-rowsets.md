---
title: "Obsługa zestawów wierszy schematu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b4dc655710c9c9cc4bb9a2549136f772b192f739
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="supporting-schema-rowsets"></a>Obsługa zestawów wierszy schematu
Zestawy wierszy schematu umożliwiają konsumentów uzyskać informacje o magazynie danych bez uprzedniego uzyskania informacji o jego struktury lub schematu. Na przykład magazynu danych może być tabel zorganizowane w hierarchii zdefiniowanej przez użytkownika, więc nie byłoby żaden sposób zapewnić wiedzę na temat schematu z wyjątkiem odczytując go. (Inny przykład należy pamiętać, że kreatorów Visual C++ zestawów wierszy schematu do generowania metody dostępu dla użytkownika.) Aby zezwolić na odbiorców to zrobić, obiekt sesji dostawcy udostępnia metody na [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) interfejsu. W aplikacji Visual C++, możesz użyć [idbschemarowsetimpl —](../../data/oledb/idbschemarowsetimpl-class.md) klasy do zaimplementowania **IDBSchemaRowset**.  
  
 `IDBSchemaRowsetImpl` obsługuje następujące metody:  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) sprawdza poprawność ograniczeń dla zestawu wierszy schematu.  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementuje funkcję twórcy obiektu COM dla obiekt określony przez parametr szablonu.  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) określa ograniczenia, które obsługuje w zestawie wierszy określonego schematu.  
  
-   [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) zwraca zestaw wierszy schematu (dziedziczone z interfejsu).  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) zwraca listę zestawów wierszy schematu dostępne dla `IDBSchemaRowsetImpl::GetRowset` (dziedziczone z interfejsu).  
  
## <a name="atl-ole-db-provider-wizard-support"></a>Obsługa kreatora dostawcy ATL OLE DB  
 ATL OLE DB dostawcy Kreator tworzy trzy klasy schematu w pliku nagłówka sesji:  
  
-   **C** *nazwa_skrócona* **SessionTRSchemaRowset**  
  
-   **C** *nazwa_skrócona* **SessionColSchemaRowset**  
  
-   **C** *nazwa_skrócona* **SessionPTSchemaRowset**  
  
 Te klasy odpowiadać na żądania klienta dla informacji o schemacie; należy pamiętać, że ze specyfikacją OLE DB wymaga obsługiwać te zestawy wierszy schematu trzy:  
  
-   **C** *nazwa_skrócona* **SessionTRSchemaRowset** obsługuje żądania, aby uzyskać informacje dotyczące tabeli ( `DBSCHEMA_TABLES` zestaw wierszy schematu).  
  
-   **C** *nazwa_skrócona* **SessionColSchemaRowset** obsługuje żądania, aby uzyskać informacje dotyczące kolumn ( **DBSCHEMA_COLUMNS** zestaw wierszy schematu). Kreator udostępnia przykładowy implementacji dla tych klas, które zwrócić informacje o schemacie dla dostawcy systemu DOS.  
  
-   **C** *nazwa_skrócona* **SessionPTSchemaRowset** obsługuje żądania informacji schematu o typ dostawcy ( **DBSCHEMA_PROVIDER_TYPES** schematu zestaw wierszy). Domyślna implementacja kreatora zwraca `S_OK`.  
  
 Można dostosować te klasy do obsługi informacji o schemacie właściwe dla dostawcy usługi:  
  
-   W **C***nazwa_skrócona***SessionTRSchemaRowset**, musisz wypełnić pola katalogu, tabeli i opis (**trData.m_szType**, **trData.m_szTable** , i **trData.m_szDesc**). Przykład generowane przez Kreatora używa tylko jeden wiersz (tabeli). Inni dostawcy mogą zwracać więcej niż jedna tabela.  
  
-   W **C***nazwa_skrócona***SessionColSchemaRowset**, przekaż nazwę tabeli jako **DBID**.  
  
## <a name="setting-restrictions"></a>Ustawianie ograniczeń  
 Ważne pojęcia w Obsługa zestawów wierszy schematu jest ustawienie ograniczenia, które możesz wykonać przy użyciu `SetRestrictions`. Ograniczenia Zezwalaj klientom pobieranie tylko pasujących wierszy (na przykład znaleźć wszystkie kolumny w tabeli "MyTable"). Ograniczenia są opcjonalne, a w przypadku, w których żaden nie jest obsługiwane (ustawienie domyślne), zwracane są wszystkie dane zawsze. Na przykład dostawcy, który obsługuje ograniczenia zobacz [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) próbki.  
  
## <a name="setting-up-the-schema-map"></a>Konfigurowanie mapy schematu  
 Konfigurowanie mapy schematu, takie jak ta, w Session.h w UpdatePV:  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 Do obsługi **IDBSchemaRowset**, musi obsługiwać `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, i **DBSCHEMA_PROVIDER_TYPES**. Zestawy wierszy schematu dodatkowe można dodać, według uznania.  
  
 Deklarowanie klasy zestawu wierszy schematu z `Execute` metody, takie jak `CUpdateSessionTRSchemaRowset` w UpdatePV:  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 Należy pamiętać, że `CUpdateSession` dziedziczy `IDBSchemaRowsetImpl`, więc wszystkie ograniczenia obsługi metody. Przy użyciu `CSchemaRowsetImpl`, zadeklarować trzech klas podrzędnych (wymienione w powyższej mapie schematu): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, i `CUpdateSessionPTSchemaRowset`. Każda z tych klas podrzędnych ma `Execute` metoda obsługująca zestawy odpowiednich ograniczeń (kryteria wyszukiwania). Każdy `Execute` metoda porównuje wartości `cRestrictions` i `rgRestrictions` parametrów. Zobacz opis tych parametrów w [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
 Aby uzyskać więcej informacji o tym, które odpowiadają ograniczenia wierszy określonego schematu, zapoznaj się spis zestaw wierszy schematu identyfikatorów GUID w [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty* w Zestaw Windows SDK.  
  
 Na przykład, jeśli użytkownik obsługiwane **nazwa_tabeli** ograniczenia `DBSCHEMA_TABLES`, należy wykonać następujące czynności:  
  
 Po pierwsze, wyszukiwanie `DBSCHEMA_TABLES` i zobacz, czy obsługuje ona cztery ograniczenia (w kolejności).  
  
|Ograniczenie zestawu wierszy schematu|Wartość ograniczenia|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG**|0x1 (1 binarny)|  
|**TABLE_SCHEMA**|0x2 (binarne 10)|  
|**TABLE_NAME**|0x4 (binarne 100)|  
|**TABLE_TYPE**|0x8 (binarne 1000)|  
  
 Następnie należy pamiętać, że jeden bit dla każdego ograniczenia. Aby można było obsługiwać **nazwa_tabeli** , zwróci 0x4 w `rgRestrictions` elementu. Jeśli użytkownik obsługiwane **TABLE_CATALOG** i **nazwa_tabeli**, zwróci 0x5 (101 binarny).  
  
 Domyślnie implementacja zwraca 0 (nie obsługuje żadnych ograniczeń) dla dowolnego żądania. UpdatePV jest przykładem dostawcy, który obsługuje ograniczenia.  
  
### <a name="example"></a>Przykład  
 Ten kod jest pobierana z [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) próbki. UpdatePv obsługuje trzy zestawy wierszy schematu wymagane: `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, i **DBSCHEMA_PROVIDER_TYPES**. Na przykład sposobu wdrażania w dostawcy obsługi schematu w tym temacie prezentująca implementacja **DBSCHEMA_TABLE** zestawu wierszy.  
  
> [!NOTE]
>  Przykładowy kod mogą być inne niż wymienione w tym miejscu; Przykładowy kod powinno być traktowane jako bardziej zaktualizowanej wersji.  
  
 Pierwszym krokiem podczas dodawania obsługi schematu jest ustalenie ograniczenia, które będą obsługiwać. Aby ustalić, które ograniczenia są dostępne dla użytkownika zestaw wierszy schematu, przyjrzeć się ze specyfikacją OLE DB dla definicji **IDBSchemaRowset**. Następujące główne definicji Zobacz temat tabeli zawierającej kolumny ograniczeń, liczba ograniczeń i nazwę zestawu wierszy schematu. Wybierz żądane do obsługi i zanotuj liczbę ograniczenia i ograniczenie kolumny zestawu wierszy schematu. Na przykład `DBSCHEMA_TABLES` obsługuje cztery ograniczenia (**TABLE_CATALOG**, **TABLE_SCHEMA**, **nazwa_tabeli**, i **TABLE_TYPE** ):  
  
```  
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,   
   ULONG* rgRestrictions)  
{  
    for (ULONG l=0; l<cRestrictions; l++)  
    {  
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
            rgRestrictions[l] = 0x0C;  
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))  
                 rgRestrictions[l] = 0x04;  
             else if (InlineIsEqualGUID(rguidSchema[l],  
                                        DBSCHEMA_PROVIDER_TYPES))  
                      rgRestrictions[l] = 0x00;  
   }  
}  
```  
  
 Bit reprezentuje każdej kolumny ograniczenia. Jeśli mają być obsługiwane ograniczenie (to znaczy można badać przy jego), ustawić tego bit na wartość 1. Jeśli nie chcesz obsługiwać ograniczenie, tego bit należy ustawić na zero. W wierszu powyższego kodu obsługuje UpdatePV **nazwa_tabeli** i **TABLE_TYPE** ograniczenia dotyczące `DBSCHEMA_TABLES` zestawu wierszy. Są to czwarty ograniczenia (maska bitowa 1000) i innych (maska bitowa 100). W związku z tym maski bitów dla UpdatePv jest 1100 (lub 0x0C):  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 Następujące `Execute` funkcji jest podobne do zestawów wierszy regularnego. Masz trzech argumentów: `pcRowsAffected`, `cRestrictions`, i `rgRestrictions`. `pcRowsAffected` Zmiennej jest parametrem wyjściowym dostawca może zwracać liczbę wierszy w zestawie wierszy schematu. `cRestrictions` Parametr jest parametrem wejściowym zawierającą liczbę ograniczenia przekazywane przez klienta do dostawcy. `rgRestrictions` Parametr jest tablicą **VARIANT** wartości, które zawierają wartości ograniczeń.  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions` Zmienna jest oparta na całkowitą liczbę ograniczeń dla zestawu wierszy schematu, niezależnie od tego, czy dostawca obsługuje je. Ponieważ UpdatePv obsługuje dwa ograniczenia (trzecia i czwarta), ten kod wyszukuje tylko `cRestrictions` o wartości większej lub równej 3.  
  
 Wartość **nazwa_tabeli** ograniczeń są przechowywane w `rgRestrictions[2]` (ponownie trzeci ograniczeń w tablicę wartości nieujemnych to 2). Należy sprawdzić, czy nie ma ograniczenia `VT_EMPTY` do faktycznie jego obsługi. Należy pamiętać, że **VT_NULL** nie jest równa `VT_EMPTY`. **VT_NULL** określa wartość prawidłowym ograniczeniem.  
  
 Definicja UpdatePv Nazwa tabeli jest pełną ścieżkę do pliku tekstowego. Wyodrębnij wartość ograniczenia, a następnie spróbuj otworzyć plik, aby upewnić się, że plik istnieje faktycznie. Jeśli plik nie istnieje, zwracany `S_OK`. To rozwiązanie może wydawać się nieco z poprzednimi wersjami, ale jakie kod naprawdę informuje klienta jest czy nie było żadnych tabel obsługiwanych przez określona nazwa. `S_OK` Return oznacza, że kod wykonane prawidłowo.  
  
```  
USES_CONVERSION;  
enum {  
            sizeOfszFile = 255  
};  
CTABLESRow  trData;  
FILE        *pFile = NULL;  
TCHAR       szFile[ sizeOfszFile ];  
errcode     err = 0;  
  
// Handle any restrictions sent to us. This only handles  
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th   
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets   
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04   
// for a total of (0x0C)  
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)  
{  
    CComBSTR bstrName = rgRestrictions[2].bstrVal;  
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))  
    {  
        // Check to see if the file exists  
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));  
        if (szFile[0] == _T('\0') ||   
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))  
        {  
            return S_OK;// Their restriction was invalid return no data  
        }  
        else  
        {  
            fclose(pFile);  
        }  
    }  
}  
```  
  
 Obsługa ograniczeń czwarty (**TABLE_TYPE**) jest podobny do ograniczeń trzecich. Sprawdź, czy wartość nie jest `VT_EMPTY`. To ograniczenie zwraca tylko z typem tabeli **tabeli**. Aby określić prawidłowe wartości dla `DBSCHEMA_TABLES`, Szukaj w dodatku B *OLE DB Podręcznik programisty* w **tabel** sekcji zestawu wierszy.  
  
```  
// TABLE_TYPE restriction:  
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)  
{  
    CComBSTR bstrType = rgRestrictions[3].bstrVal;  
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))  
    {  
        // This is kind of a blind restriction.  
        // This only actually supports  
        // TABLES so if you get anything else,   
        // just return an empty rowset.  
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)  
            return S_OK;  
    }  
}  
```  
  
 Jest to, gdzie faktycznie utworzyć wpis wierszu w zestawie wierszy. Zmienna `trData` odpowiada **CTABLESRow**, struktury zdefiniowane w szablonach dostawcy OLE DB. **CTABLESRow** odpowiada **tabel** definicji zestawu wierszy dodatek b ze specyfikacją OLE DB. Masz tylko jeden wiersz można dodać, ponieważ jedna tabela może obsługiwać tylko w czasie.  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV ustawia tylko trzy kolumny: **nazwa_tabeli**, **TABLE_TYPE**, i **opis**. Należy następnie zanotuj kolumny, dla których zwracają informacje, ponieważ te informacje są niezbędne podczas implementowania `GetDBStatus`:  
  
```  
    _ATLTRY  
    {  
        m_rgRowData.Add(trData);  
    }  
    _ATLCATCHALL()  
    {  
        return E_OUTOFMEMORY;  
    }  
    //if (!m_rgRowData.Add(trData))  
    //    return E_OUTOFMEMORY;  
    *pcRowsAffected = 1;  
    return S_OK;  
}  
```  
  
 `GetDBStatus` Funkcji jest bardzo ważne dla poprawnego działania zestawu wierszy schematu. Ponieważ nie zwraca dane dla każdej kolumny w **tabel** zestawu wierszy, należy określić, które kolumny zwracane dane i nie chcesz.  
  
```  
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)  
{  
    ATLASSERT(pColInfo != NULL);  
  
    switch(pColInfo->iOrdinal)  
    {  
    case 3:     // TABLE_NAME  
    case 4:     // TABLE_TYPE  
    case 6:     // DESCRIPTION  
        return DBSTATUS_S_OK;  
        break;  
    default:  
        return DBSTATUS_S_ISNULL;  
    break;  
    }  
}  
```  
  
 Ponieważ Twoje `Execute` funkcja zwraca dane dotyczące **nazwa_tabeli**, **TABLE_TYPE**, i **opis** pola z **tabel**wierszy można Szukaj dodatek b ze specyfikacją OLE DB i określić (licząc od góry w) są porządkowe 3, 4 i 6. Dla każdego z tych kolumn, zwróć **DBSTATUS_S_OK**. W przypadku wszystkich innych kolumn, zwracają **DBSTATUS_S_ISNULL**. Ważne jest, aby zwrócić ten stan, ponieważ klient nie może zrozumieć, czy wartość powrócisz jest **NULL** lub inny. Ponownie, należy pamiętać, że **NULL** nie jest odpowiednikiem puste.  
  
 Aby uzyskać więcej informacji na temat interfejsu zestawu wierszy schematu OLE DB, zobacz [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) interfejsu OLE DB Podręcznik programisty.  
  
 Aby dowiedzieć się jak klienci mogą korzystać **IDBSchemaRowset** metod, zobacz [uzyskiwanie metadanych za pomocą zestawów wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).  
  
 Na przykład dostawcę, który obsługuje zestawów wierszy schematu zobacz [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)