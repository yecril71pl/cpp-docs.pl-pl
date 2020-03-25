---
title: 'Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: 9d19328fb82503519fd8eca083e0dd11e10883ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212956"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano sposób tworzenia klasy zestawu rekordów dla wstępnie zdefiniowanego zapytania (nazywanego czasem procedurą składowaną, jak w Microsoft SQL Server).

> [!NOTE]
>  Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli zaimplementowano pobieranie wierszy zbiorczych, proces jest bardzo podobny. Aby zrozumieć różnice między zestawami rekordów, które implementują pobieranie wierszy zbiorczych, a tym, które nie, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Niektóre systemy zarządzania bazami danych (DBMS) umożliwiają tworzenie wstępnie zdefiniowanego zapytania i wywoływanie go z programów takich jak funkcja. Zapytanie ma nazwę, może przyjmować parametry i może zwracać rekordy. W procedurze opisanej w tym temacie opisano sposób wywoływania wstępnie zdefiniowanego zapytania, które zwraca rekordy (a także przyjmuje parametry).

Klasy baz danych nie obsługują aktualizacji wstępnie zdefiniowanych zapytań. Różnica między wstępnie zdefiniowanym zapytaniem migawki a wstępnie zdefiniowanym zapytaniem nie jest aktualizowana, ale czy zmiany wprowadzone przez innych użytkowników (lub inne zestawy rekordów w programie) są widoczne w zestawie rekordów.

> [!TIP]
>  Zestaw rekordów nie jest potrzebny do wywołania wstępnie zdefiniowanego zapytania, które nie zwraca rekordów. Przygotuj instrukcję SQL zgodnie z poniższym opisem, ale wykonaj ją, wywołując `CDatabase` funkcji składowej [ExecuteSql by](../../mfc/reference/cdatabase-class.md#executesql).

Można utworzyć pojedynczą klasę zestawu rekordów, aby zarządzać wywołaniem wstępnie zdefiniowanego zapytania, ale musisz samodzielnie wykonać część pracy. Kreatory nie obsługują tworzenia klasy specjalnie do tego celu.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Aby utworzyć klasę do wywoływania wstępnie zdefiniowanego zapytania (procedura składowana)

1. Użyj [Kreatora użytkownika ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **klasy Dodaj** , aby utworzyć klasę zestawu rekordów dla tabeli, która współużytkuje większość kolumn zwracanych przez zapytanie. Dzięki temu można zacząć od początku.

1. Ręcznie Dodaj elementy członkowskie danych pola dla wszystkich kolumn w dowolnych tabelach zwracanych przez zapytanie, ale nie zostały utworzone przez kreatora.

   Na przykład, jeśli zapytanie zwróci trzy kolumny z dwóch dodatkowych tabel, Dodaj sześć elementów członkowskich danych (odpowiednich typów danych) do klasy.

1. Ręcznie Dodaj wywołania funkcji [RFX](../../data/odbc/record-field-exchange-rfx.md) w funkcji członkowskiej [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) klasy, jeden odpowiadający typowi danych każdego dodawanego elementu członkowskiego danych pola.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Musisz znać typy danych i kolejność kolumn zwracanych w zestawie wyników. Kolejność wywołań funkcji RFX w `DoFieldExchange` musi być zgodna z kolejnością kolumn zestawu wyników.

1. Ręcznie Dodaj inicjalizacje dla nowych elementów członkowskich danych pola w konstruktorze klas zestawu rekordów.

   Należy również zwiększyć wartość inicjującą dla elementu członkowskiego danych [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) . Kreator zapisuje inicjalizację, ale obejmuje tylko elementy członkowskie danych pól, które dodaje do użytkownika. Na przykład:

    ```cpp
    m_nFields += 6;
    ```

   W tym miejscu nie należy inicjować niektórych typów danych, na przykład `CLongBinary` lub tablic bajtowych.

1. Jeśli zapytanie pobiera parametry, Dodaj element członkowski danych parametrów dla każdego parametru, wywołanie funkcji RFX dla każdego z nich i inicjalizację dla każdego z nich.

1. Należy zwiększyć `m_nParams` dla każdego dodanego parametru, ponieważ `m_nFields` do dodanych pól w kroku 4 tej procedury. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ręcznie Napisz ciąg instrukcji SQL o następującej postaci:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   gdzie **call** jest słowem kluczowym ODBC, **proc-Name** to nazwa zapytania, która jest znana w źródle danych, a elementy "?" są symbolami zastępczymi wartości parametrów dostarczanych do zestawu rekordów w czasie wykonywania (jeśli istnieje). Poniższy przykład przygotowuje symbol zastępczy dla jednego parametru:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. W kodzie, który otwiera zestaw rekordów, ustaw wartości elementów członkowskich danych parametrów zestawu rekordów, a następnie wywołaj funkcję elementu członkowskiego `Open`, przekazując ciąg SQL dla parametru *lpszSQL* . Zamiast tego Zastąp ciąg zwracany przez funkcję członkowską `GetDefaultSQL` w klasie.

W poniższych przykładach pokazano procedurę wywoływania wstępnie zdefiniowanego zapytania o nazwie `Delinquent_Accts`, która przyjmuje jeden parametr dla numeru okręgu sprzedaży. To zapytanie zwraca trzy kolumny: `Acct_No`, `L_Name`, `Phone`. Wszystkie kolumny pochodzą z tabeli Customers.

Następujący zestaw rekordów określa elementy członkowskie danych pola dla kolumn zwracanych przez zapytanie i parametr dla numeru okręgu sprzedaży żądany w czasie wykonywania.

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

Ta deklaracja klasy jest zapisywany przez kreatora, z wyjątkiem `m_lDistParam` dodawane ręcznie. Inne elementy członkowskie nie są wyświetlane w tym miejscu.

W następnym przykładzie pokazano inicjalizacje elementów członkowskich danych w konstruktorze `CDelinquents`.

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

Zanotuj inicjalizacje dla [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) i [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Kreator inicjuje `m_nFields`; zainicjowano `m_nParams`.

W następnym przykładzie przedstawiono funkcje RFX w `CDelinquents::DoFieldExchange`:

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

Oprócz wykonywania wywołań RFX dla trzech zwracanych kolumn ten kod zarządza wiązaniem parametru, który jest przekazywany w czasie wykonywania. Parametr jest kluczem do kolumny `Dist_No` (numer okręgu).

W następnym przykładzie pokazano, jak skonfigurować ciąg SQL i jak używać go do otwierania zestawu rekordów.

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

Ten kod tworzy migawkę, przekazuje jej parametr uzyskany wcześniej od użytkownika i wywołuje wstępnie zdefiniowane zapytanie. Gdy zapytanie zostanie uruchomione, zwraca rekordy dla określonego okręgu sprzedaży. Każdy rekord zawiera kolumny dla numeru konta, nazwisko klienta i numer telefonu klienta.

> [!TIP]
>  Możesz chcieć obsłużyć wartość zwracaną (parametr wyjściowy) z procedury składowanej. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
