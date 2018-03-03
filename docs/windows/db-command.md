---
title: "db_command — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.db_command
dev_langs:
- C++
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87209d673da47827723198697a26300d4056d3d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dbcommand"></a>db_command
Tworzy polecenia OLE DB.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ db_command(   
   command,   
   name,   
   source_name,   
   hresult,   
   bindings,   
   bulk_fetch)  
]  
```  
  
#### <a name="parameters"></a>Parametry  
 `command`  
 Ciąg polecenia zawierające tekst polecenia OLE DB. Jest to prosty przykład:  
  
```  
[ db_command ( command = "Select * from Products" ) ]  
```  
  
 *Polecenia* ma następującą składnię:  
  
```  
binding parameter block 1  
   OLE DB command  
binding parameter block 2  
   continuation of OLE DB command  
binding parameter block 3  
...  
```  
  
 A *bloku parametrów wiązania* jest zdefiniowane w następujący sposób:  
  
 **([** `bindtype` **]** *szVar1* [*, szVar2* [, *nVar3* [,...]]] **)**  
  
 gdzie:  
  
 **(** oznacza początek bloku powiązania danych.  
  
 **[** `bindtype` **]** jest jednym z następujących ciągów bez uwzględniania wielkości liter:  
  
-   **[db_column —]**  wiąże wszystkich zmiennych Członkowskich z kolumną w zestawie wierszy.  
  
-   **[bindto]**  (taki sam jak **[db_column —]**).  
  
-   **[in]**  wiąże zmiennych Członkowskich jako parametry wejściowe.  
  
-   **[out]**  wiąże zmiennych Członkowskich jako parametry wyjściowe.  
  
-   **[w, out]**  wiąże zmiennych Członkowskich jako parametry wejścia/wyjścia.  
  
 *SzVarX* rozpoznawane jako zmienna elementu członkowskiego w bieżącym zakresie.  
  
 **)** oznacza koniec bloku powiązania danych.  
  
 Jeśli ciąg polecenia zawiera co najmniej jeden specyfikatory takich jak [in] [limit] lub [We/Wy], **db_command —** kompiluje mapy parametru.  
  
 Jeśli ciąg polecenia zawiera jeden lub więcej parametrów, takich jak [db_column —] lub [bindto] **db_command —** generuje zestawu wierszy i mapowanie dostępu do obsługi tych powiązania zmiennych. Zobacz [db_accessor —](../windows/db-accessor.md) Aby uzyskać więcej informacji.  
  
> [!NOTE]
>  [`bindtype`] składni i `bindings` parametru nie są prawidłowe w przypadku korzystania z **db_command —** na poziomie klasy.  
  
 Oto kilka przykładów bloki parametru wiązania. Poniższy przykład wiąże `m_au_fname` i `m_au_lname` elementy członkowskie danych do `au_fname` i `au_lname` kolumn, odpowiednio, z tabeli Autorzy w bazie danych pubs:  
  
```  
TCHAR m_au_fname[21];  
TCHAR m_au_lname[41];  
TCHAR m_state[3] = 'CA';  
  
[db_command (  
   command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \  
   "FROM dbo.authors " \  
   "WHERE state = ?([in]m_state)")  
```  
  
 ]  
  
 *Nazwa* (opcjonalnie)  
 Nazwa dojście służy do pracy z zestawu wierszy. Jeśli określisz *nazwa*, **db_command —** generuje klasę z określonym *nazwa*, które mogą służyć do przechodzenia w zestawie wierszy lub wykonywać wiele akcji kwerendy. Jeśli nie określisz *nazwa*, nie będzie można przywrócić więcej niż jeden wiersz wyników użytkownika.  
  
 *source_name* (opcjonalnie)  
 `CSession` Zmiennej lub wystąpienia klasy, która ma `db_source` atrybut zastosowany do niego, na którym wykonuje polecenie. Zobacz [db_source —](../windows/db-source.md).  
  
 **db_command —** sprawdza, upewnij się, że zmienna dla *source_name* jest poprawny, dlatego określonej zmiennej musi należeć do funkcji lub zakresie globalnym.  
  
 `hresult`(opcjonalnie)  
 Identyfikuje zmienna, która odbierze `HRESULT` tego polecenia bazy danych. Jeśli zmienna nie istnieje, jej zostaną automatycznie dodane przez atrybut.  
  
 *powiązania* (opcjonalnie)  
 Służy do rozdzielenia parametrów powiązanie polecenia OLE DB.  
  
 Jeśli określono wartość dla `bindings`, **db_command —** będzie analizować skojarzona wartość i nie można przeanalizować [`bindtype`] parametru. To użycie umożliwia przy użyciu składni dostawcy OLE DB. Aby wyłączyć analizowania bez wiązania parametrów, określ **powiązania = ""**.  
  
 Jeśli nie określisz wartości `bindings`, **db_command —** będzie analizować bloku parametrów powiązania, wyszukiwanie "**(**", a następnie **[** `bindtype` **]**  w nawiasy kwadratowe, przez co najmniej jeden poprzednio zadeklarowana C++ zmienne Członkowskie, a następnie "**)**". Cały tekst w nawiasach zostanie usunięte z polecenia wynikowy, a te parametry ma być użyty do utworzenia powiązania kolumny i parametrów dla tego polecenia.  
  
 *bulk_fetch*(opcjonalnie)  
 Wartość całkowita określająca liczbę wierszy do pobrania.  
  
 Wartość domyślna to 1, który określa pobieranie pojedynczy wiersz (zestaw wierszy będzie typu [CRowset](../data/oledb/crowset-class.md)).  
  
 Wartość większą niż 1 określa zbiorcze pobieranie z wiersza. Zbiorcze pobieranie z wiersza odwołuje się do możliwość pobrania wielu dojść do wierszy zbiorcze zestawy wierszy (zestaw wierszy będzie typu [cbulkrowset —](../data/oledb/cbulkrowset-class.md) i wywoła `SetRows` o określoną liczbę wierszy).  
  
 Jeśli *bulk_fetch* jest mniejsza niż jedna `SetRows` , którą będzie zwracać zera.  
  
## <a name="remarks"></a>Uwagi  
 **db_command —** tworzy [CCommand](../data/oledb/ccommand-class.md) obiektu, który jest używany przez konsumenta OLE DB do wykonania polecenia.  
  
 Można użyć **db_command —** z zakresem klasy lub funkcji; podstawowa różnica polega na zakresie `CCommand` obiektu. W zakresie funkcji dane, takie jak powiązania przerwanie na końcu funkcji. Klasy OLE DB szablon klienta obejmują zarówno klasy, jak i funkcja zakres użycia **CCommand <>**, ale argumenty szablonu różnią się w przypadku funkcji i klasy. W przypadku funkcji, powiązania nie zostaną wprowadzone **akcesor** zmiennych lokalnych, który obejmuje podczas wywnioskuje użycia klasy `CAccessor`-klasy jako argument. Gdy jest używany jako atrybut class, **db_command —** działa w połączeniu z **db_column —**.  
  
 **db_command —** może służyć do wykonywania poleceń, które nie zwracają zestaw wyników.  
  
 Gdy dostawca atrybutu konsumenta stosuje ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, gdzie *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasy o nazwie *YourClassName*, co wynika ze \_ *YourClassName*metody dostępu.  W widoku klasy zostanie wyświetlona zarówno klasy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje polecenie, które wybiera imiona i nazwiska z tabeli, jeśli odpowiada "CA" w kolumnie Stan. **db_command —** tworzy i odczytuje zestawu wierszy, na którym należy wywołać generowane przez Kreatora funkcji takich jak [OpenAll i CloseAll](../data/oledb/consumer-wizard-generated-methods.md), jak również `CRowset` takich jak funkcje Członkowskie [MoveNext](../data/oledb/crowset-movenext.md).  
  
 Należy pamiętać, że ten kod musisz podać własne parametry połączenia, które nawiązuje połączenie z bazą danych pubs. Aby uzyskać informacje, jak to zrobić w środowisku programistycznym, zobacz [jak: połączenie z bazą danych Eksploratora serwera](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74) i [porady: dodawanie nowych połączeń danych w Eksploratorze Explorer/bazy danych serwera](http://msdn.microsoft.com/en-us/fb2f513b-ddad-4142-911e-856bba0054c8).  
  
```  
// db_command.h  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
#pragma once  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
  
struct CAuthors {  
   // In order to fix several issues with some providers, the code below may bind  
   // columns in a different order than reported by the provider  
  
   DBSTATUS m_dwau_lnameStatus;  
   DBSTATUS m_dwau_fnameStatus;  
   DBLENGTH m_dwau_lnameLength;  
   DBLENGTH m_dwau_fnameLength;  
  
   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];  
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];  
  
   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];  
  
   void GetRowsetProperties(CDBPropSet* pPropSet) {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   }  
};  
```  
  
## <a name="example"></a>Przykład  
  
```  
// db_command.cpp  
// compile with: /c  
#include "db_command.h"  
  
int main(int argc, _TCHAR* argv[]) {  
   HRESULT hr = CoInitialize(NULL);  
  
   // Instantiate rowset  
   CAuthors rs;  
  
   // Open rowset and move to first row  
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));  
   hr = rs.OpenAll();  
   hr = rs.MoveFirst();  
  
   // Iterate through the rowset  
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {  
      // Print out the column information for each row  
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);  
      hr = rs.MoveNext();  
   }  
  
   rs.CloseAll();  
   CoUninitialize();  
}  
```  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto `db_source` klasy źródła danych `CMySource`, i `db_command` w klasach polecenia `CCommand1` i `CCommand2`.  
  
```  
// db_command_2.cpp  
// compile with: /c  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
// class usage for both db_source and db_command  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
struct CMySource {  
   HRESULT OpenDataSource() {  
      return S_OK;  
   }  
};  
  
[db_command(command = "SELECT * FROM Products")]  
class CCommand1 {};  
  
[db_command(command = "SELECT FNAME, LNAME FROM Customers")]  
class CCommand2 {};  
  
int main() {  
   CMySource s;  
   HRESULT hr = s.OpenDataSource();  
   if (SUCCEEDED(hr)) {  
      CCommand1 c1;  
      hr = c1.Open(s);  
  
      CCommand2 c2;  
      hr = c2.Open(s);  
   }  
  
   s.CloseDataSource();  
}  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, elementu członkowskiego, metoda, lokalnego|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
