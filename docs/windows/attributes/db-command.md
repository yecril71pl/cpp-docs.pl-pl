---
title: db_command (atrybut C++ COM)
ms.date: 07/10/2018
f1_keywords:
- vc-attr.db_command
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
ms.openlocfilehash: 5910e72b10d5b849d203d088564d79d0f80a7961
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504593"
---
# <a name="db_command"></a>db_command

Tworzy polecenie OLE DB.

## <a name="syntax"></a>Składnia

```cpp
[ db_command(command, name, source_name, hresult, bindings, bulk_fetch)
]
```

### <a name="parameters"></a>Parametry

*dotyczące*<br/>
Ciąg polecenia zawierający tekst polecenia OLE DB. Prosty przykład:

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

Składnia *polecenia* jest następująca:

> powiązanie bloku parametrów 1 \
> &nbsp;&nbsp;Polecenie OLE DB \
> powiązanie parametru — blok 2 \
> &nbsp;&nbsp;Kontynuacja polecenia OLE DB \
> powiązanie bloku parametrów 3 \
> ...

*Blok parametrów powiązania* jest definiowany w następujący sposób:

> **( \[ ** *BindType* **]** *szVar1* \[ , *szVar2* \[ , *nVar3* \[ ,...]]] **)**

gdzie:

- **(** oznacza początek bloku powiązania danych.

- **\[***BindType* **]** to jeden z następujących ciągów bez uwzględniania wielkości liter:

  - ** \[ Db_column]** wiąże wszystkie zmienne Członkowskie z kolumną w zestawie wierszy.

  - ** \[ BindTo]** (tak samo jak ** \[ Db_column]**).

  - ** \[ in]** wiąże Zmienne Członkowskie jako parametry wejściowe.

  - ** \[ out]** tworzy powiązania zmiennych składowych jako parametrów wyjściowych.

  - ** \[ w, out]** tworzy zmienne składowe jako parametry wejściowe/wyjściowe.

- *szVarX*, *nVarX* jest rozpoznawana jako zmienna członkowska w bieżącym zakresie.

- **)** oznacza koniec bloku powiązania danych.

Jeśli ciąg polecenia zawiera jeden lub więcej specyfikatorów, takich jak \[ in], \[ out] lub \[ in/out], **db_command** kompiluje mapę parametrów.

Jeśli ciąg polecenia zawiera jeden lub więcej parametrów, takich jak \[ Db_column] lub \[ BindTo], **db_command** generuje zestaw wierszy i mapę dostępu, aby obsłużyć te zmienne powiązane. Aby uzyskać więcej informacji, zobacz [db_accessor](db-accessor.md) .

> [!NOTE]
> \[*BindType*] Składnia i parametr *bindings* są nieprawidłowe, gdy jest używany **db_command** na poziomie klasy.

Oto kilka przykładów bloków parametrów powiązań. Poniższy przykład wiąże `m_au_fname` i `m_au_lname` składowe danych z i `au_fname` odpowiednio do `au_lname` kolumn w tabeli autorów w bazie danych pubs:

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")
]
```

*Nazwij*<br/>
Obowiązkowe Nazwa dojścia używanego do pracy z zestawem wierszy. Jeśli określisz *nazwę*, **db_command** generuje klasę o określonej *nazwie*, która może być używana do przechodzenia zestawu wierszy lub wykonywania wielu zapytań akcji. Jeśli *Nazwa*nie zostanie określona, nie będzie możliwe zwrócenie więcej niż jednego wiersza wyników do użytkownika.

*source_name*<br/>
Obowiązkowe `CSession` Zmienna lub wystąpienie klasy, `db_source` do której zastosowano polecenie. Zobacz [db_source](db-source.md).

**db_command** sprawdza, czy zmienna użyta dla *source_name* jest prawidłowa, więc określona zmienna powinna być w funkcji lub globalnym zakresie.

*wynik*<br/>
Obowiązkowe Identyfikuje zmienną, która będzie otrzymywać wartość HRESULT tego polecenia bazy danych. Jeśli zmienna nie istnieje, zostanie automatycznie wprowadzona przez atrybut.

*powiązań*<br/>
Obowiązkowe Umożliwia rozdzielenie parametrów powiązania za pomocą polecenia OLE DB.

Jeśli określisz wartość *powiązań*, **db_command** przeanalizuje skojarzoną wartość i nie przeanalizuje parametru \[ *BindType*]. To użycie umożliwia użycie składni dostawcy OLE DB. Aby wyłączyć analizowanie bez parametrów powiązań, określ `Bindings=""` .

Jeśli nie określisz wartości *powiązań*, **db_command** przeanalizuje Blok parametrów powiązania, szukając znaku "**(**", po którym następuje **\[** _powiązanietype_**]** w nawiasach, po którym następuje co najmniej jedna zadeklarowana wcześniej zmienna członkowska języka C++, po której następuje znak "**)**". Cały tekst między nawiasami zostanie usunięty z wyniku polecenia i te parametry będą używane do konstruowania powiązań kolumn i parametrów dla tego polecenia.

*bulk_fetch*<br/>
Obowiązkowe Wartość całkowita określająca liczbę wierszy do pobrania.

Wartość domyślna to 1, która określa Pobieranie pojedynczego wiersza (zestaw wierszy będzie typu [CRowset](../../data/oledb/crowset-class.md)).

Wartość większa niż 1 określa pobieranie wierszy zbiorczych. Pobieranie wierszy zbiorczych odnosi się do zdolności zbiorczych zestawów wierszy do pobrania wielu dojść do wierszy (zestaw wierszy będzie typu [CBulkRowset](../../data/oledb/cbulkrowset-class.md) i będzie wywoływał `SetRows` określoną liczbę wierszy).

Jeśli *bulk_fetch* jest mniejsza niż 1, `SetRows` zwróci wartość zero.

## <a name="remarks"></a>Uwagi

**db_command** tworzy obiekt [CCommand](../../data/oledb/ccommand-class.md) , który jest używany przez konsumenta OLE DB do wykonania polecenia.

Można użyć **db_command** z zakresem klasy lub funkcji; Główną różnicą jest zakres `CCommand` obiektu. Wraz z zakresem funkcji dane takie jak powiązania kończą się na końcu funkcji. Użycie zakresów klasy i funkcji obejmuje OLE DB klasy szablonu konsumenta `CCommand<>` , ale argumenty szablonu różnią się w przypadku funkcji i klas. W przypadku funkcji, powiązania zostaną wykonane do obiektu, `Accessor` który składa się ze zmiennych lokalnych, podczas gdy użycie klasy spowoduje wywnioskowanie `CAccessor` klasy pochodnej jako argumentu. Gdy jest używany jako atrybut klasy, **db_command** działa w połączeniu z **Db_column**.

**db_command** może służyć do wykonywania poleceń, które nie zwracają zestawu wyników.

Gdy dostawca atrybutu konsumenta zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_ *YourClassName*, gdzie *YourClassName* jest nazwą, która została nadana klasie, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi z \_ metody dostępu *YourClassName*.  W Widok klasy są wyświetlane obie klasy.

## <a name="examples"></a>Przykłady

Ten przykład definiuje polecenie, które wybiera imiona i nazwiska z tabeli, w której kolumna State pasuje do "CA". **db_command** tworzy i odczytuje zestaw wierszy, w którym można wywołać funkcje generowane przez kreatora, takie jak [metody OpenAll i CloseAll](../../data/oledb/consumer-wizard-generated-methods.md), a także `CRowset` funkcje członkowskie, takie jak [MoveNext](../../data/oledb/crowset-class.md#movenext).

Należy zauważyć, że ten kod wymaga podania własnych parametrów połączenia, które łączą się z bazą danych pubs. Aby uzyskać informacje o tym, jak to zrobić w środowisku deweloperskim, zobacz [How to: Connect to a Database and Browse Existing objectss](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects) and [Add New Connections](/visualstudio/data-tools/add-new-connections).

```cpp
// db_command.h
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

#pragma once

[  db_source(L"your connection string"), db_command(L" \
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

Ten przykład używa `db_source` na klasie źródła danych `CMySource` i `db_command` w klasach poleceń `CCommand1` i `CCommand2` .

```cpp
// db_command_2.cpp
// compile with: /c
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>
// class usage for both db_source and db_command

[  db_source(L"your connection string"), db_command(L" \
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

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`** , członek, metoda, lokalna|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[OLE DB atrybuty konsumenta](ole-db-consumer-attributes.md)<br/>
[Atrybuty autonomiczne](stand-alone-attributes.md)
