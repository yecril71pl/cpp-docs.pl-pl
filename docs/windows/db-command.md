---
title: db_command — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/10/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_command
dev_langs:
- C++
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0b34cbd2cebea2b1c4d6bf32e61a7f496b70d7a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596271"
---
# <a name="dbcommand"></a>db_command

Tworzy polecenie OLE DB.

## <a name="syntax"></a>Składnia

```cpp
[ db_command(
   command,
   name,
   source_name,
   hresult,
   bindings,
   bulk_fetch)  
]
```

### <a name="parameters"></a>Parametry

*Polecenie*  
Polecenie ciąg zawierający tekst polecenia OLE DB. Prostym przykładem jest:

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

*Polecenia* składnia jest następująca:

> wiązanie parametru blok 1 &nbsp; &nbsp;OLE DB polecenia wiązania parametru blok 2 &nbsp; &nbsp;kontynuacji 3 blok parametrów powiązanie polecenia OLE DB...

A *blok parametrów powiązania* jest zdefiniowana w następujący sposób:

> **(\[**  *bindtype* **]** *szVar1* \[, *szVar2* \[, *nVar3* \[,...]]] **)**

gdzie:

- **(** oznacza początek bloku powiązania danych.

- **\[** *bindtype* **]** jest jednym z następujących ciągów bez uwzględniania wielkości liter:

  -   **\[db_column —]** wszystkich zmiennych składowych jest powiązana z kolumną w zestawie wierszy.

  -   **\[bindto]** (taka sama jak  **\[db_column —]**).

  -   **\[w]** wiąże zmiennych składowych jako parametry wejściowe.

  -   **\[out]** wiąże zmiennych składowych jako parametrów wyjściowych.

  -   **\[w, poza]** wiąże zmiennych składowych jako parametry wejścia/wyjścia.

- *szVarX*, *nVarX* jest rozpoznawana jako zmienną składową w bieżącym zakresie.

- **)** oznacza koniec bloku powiązania danych.

Jeśli ciąg polecenia zawiera jeden lub więcej specyfikatorów, takie jak \[w], \[out], lub \[we/wy], **db_command —** tworzy mapę parametru.

Jeśli ciąg polecenia zawiera jeden lub więcej parametrów, takich jak \[db_column —] lub \[bindto], **db_command —** generuje zestawu wierszy i mapy akcesora do obsługi tych powiązanych zmiennych. Zobacz [db_accessor —](../windows/db-accessor.md) Aby uzyskać więcej informacji.

> [!NOTE]
> \[*bindtype*] składnia i *powiązania* parametru nie są prawidłowe w przypadku korzystania z **db_command —** na poziomie klasy.

Oto kilka przykładów bloki parametru wiązania. Poniższy przykład tworzy powiązanie `m_au_fname` i `m_au_lname` elementów członkowskich danych `au_fname` i `au_lname` kolumn, odpowiednio, z tabeli Autorzy w bazie danych pubs:

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (
   command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")  
]
```

*Nazwa* (opcjonalnie)  
Nazwa uchwyt, używanej do pracy z zestawu wierszy. Jeśli określisz *nazwa*, **db_command —** generuje klasę o określonej *nazwa*, które mogą służyć do przechodzenia w zestawie wierszy lub wykonywać wiele zapytań akcji. Jeśli nie określisz *nazwa*, nie będzie możliwe do zwrócenia więcej niż jeden wiersz wyników użytkownikowi.

*source_name* (opcjonalnie)  
`CSession` Zmiennej lub wystąpienia klasy, która ma `db_source` zastosowany do niego, w którym polecenie zostanie wykonane. Zobacz [db_source —](../windows/db-source.md).

**db_command —** kontrole, aby upewnić się, że zmienna umożliwiający *source_name* jest poprawny, dlatego należy określona zmienna w funkcji lub zakresu globalnego.

*HRESULT* (opcjonalnie)  
Identyfikuje zmienna, która otrzyma wartość HRESULT dla tego polecenia bazy danych. Jeśli zmienna nie istnieje, jego zostanie automatycznie dodany przez atrybut.

*powiązania* (opcjonalnie)  
Pozwala na oddzielne Parametry wiążące polecenia OLE DB.

Jeśli określono wartość dla *powiązania*, **db_command —** będzie analizować skojarzoną wartość i nie można przeanalizować \[ *bindtype*] parametru. Użycie tych umożliwia należy użyć składni dostawcy OLE DB. Aby wyłączyć analizy bez wiązania parametrów, należy określić `Bindings=""`.

Jeśli nie określisz wartości *powiązania*, **db_command —** będzie analizować blok parametrów powiązania, wyszukiwanie "**(**", a następnie **\[** _bindtype_**]** w nawiasy kwadratowe, przez co najmniej jeden wcześniej zadeklarowanej C++ zmienne Członkowskie, a następnie "**)**". Cały tekst w nawiasach zostanie usunięta, a wynikowy polecenia, a te parametry, będą używane do konstruowania kolumny i parametru powiązania dla tego polecenia.

*bulk_fetch* (opcjonalnie)  
Wartość całkowita określająca liczbę wierszy do pobrania.

Wartość domyślna to 1, który określa pobieranie pojedynczego wiersza (zestaw wierszy będzie mieć typ [CRowset](../data/oledb/crowset-class.md)).

Określa wartość większą niż 1, zbiorcze pobieranie z wiersza. Zbiorcze pobieranie z wiersza odwołuje się do możliwości zbiorcze zestawy wierszy można pobrać dojścia do wielu wierszy (rowset będzie mieć typ [cbulkrowset —](../data/oledb/cbulkrowset-class.md) i wywoła `SetRows` o określoną liczbę wierszy).

Jeśli *bulk_fetch* jest mniejsza niż jeden `SetRows` zwróci wartość zero.

## <a name="remarks"></a>Uwagi

**db_command —** tworzy [CCommand](../data/oledb/ccommand-class.md) obiektu, który jest używany przez konsumenta OLE DB do wykonania polecenia.

Możesz użyć **db_command —** z zakresem klasy lub funkcji; główna różnica polega na zakres `CCommand` obiektu. Z zakresem funkcji danych, np. powiązania zakończenie na końcu funkcji. Klasa i funkcja użycia zakresu obejmują klasy OLE DB szablon konsumenta `CCommand<>`, ale argumentów szablonu różnią się w przypadkach, funkcji i klas. W przypadku funkcji, powiązania nie zostaną wprowadzone `Accessor` zmiennych lokalnych, która obejmuje podczas wywnioskuje użycie klasy `CAccessor`-klasy jako argument. Gdy jest używana jako atrybut class **db_command —** działa w połączeniu z **db_column —**.

**db_command —** może służyć do wykonywania poleceń, które nie zwracają zestaw wyników.

Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.

## <a name="example"></a>Przykład

W tym przykładzie definiuje polecenie, które polega na wybraniu imiona i nazwiska z tabelą, jeśli kolumna stanu odpowiada "CA". **db_command —** tworzy i odczytuje zestawu wierszy, w którym może wywołać generowane przez kreatora funkcje takie jak [openall — i closeall —](../data/oledb/consumer-wizard-generated-methods.md), a także `CRowset` takich jak funkcje Członkowskie [MoveNext](../data/oledb/crowset-movenext.md).

Należy pamiętać, że ten kod należy podać własne parametry połączenia, który nawiązuje połączenie z bazą danych pubs. Aby uzyskać informacje, jak to zrobić w środowisku programistycznym, zobacz [jak: łączenie się z bazą danych i przeglądanie istniejących obiektów](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects) i [dodać nowe połączenia](/visualstudio/data-tools/add-new-connections).

```cpp
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

```cpp
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

W tym przykładzie użyto `db_source` w klasie źródła danych `CMySource`, i `db_command` w klasach polecenia `CCommand1` i `CCommand2`.

```cpp
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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **struktury**, elementu członkowskiego, metoda, lokalne|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz także

[Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  
