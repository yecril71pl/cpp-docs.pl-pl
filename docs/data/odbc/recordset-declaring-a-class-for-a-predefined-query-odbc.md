---
title: 'Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: d4ae9f21c4bd53a8050d6f8c3765bb9823d077ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395602"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak utworzyć zestaw rekordów klasy dla wstępnie zdefiniowanego zapytania (nazywane również procedury składowanej, tak jak w programie Microsoft SQL Server).

> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli zbiorcze pobieranie z wiersza jest zaimplementowana, proces jest bardzo podobne. Aby zrozumieć różnice między zestawami rekordów, który implementuje zbiorcze pobieranie z wiersza, które nie obsługują, zobacz [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Niektóre systemy zarządzania bazami danych (DBMS) pozwalają na tworzenie wstępnie zdefiniowanego zapytania i wywołać go z Twojego programów, takich jak funkcja. Zapytanie o nazwie, może potrwać parametrów i może zwrócić rekordów. Procedury przedstawione w tym temacie opisano sposób wywoływania wstępnie zdefiniowanego zapytania, które zwraca rekordy (i prawdopodobnie przyjmuje parametry).

Klasy bazy danych nie obsługuje ich aktualizowania wstępnie zdefiniowanych zapytań. Różnica między wstępnie zdefiniowanego zapytania migawki i wstępnie zdefiniowanego zapytania dynamiczny nie jest updateability, ale czy zmiany wprowadzone przez innych użytkowników (lub innych zestawów rekordów w programie) są widoczne w twoim zestawie rekordów.

> [!TIP]
>  Zestaw rekordów do wywołania wstępnie zdefiniowanego zapytania, która nie zwraca rekordów nie jest konieczne. Przygotowanie instrukcji SQL, zgodnie z poniższym opisem, ale wykonanie go przez wywołanie metody `CDatabase` funkcja elementu członkowskiego [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Można utworzyć klasy jednym zestawie rekordów do zarządzania, wywołanie wstępnie zdefiniowanego zapytania, ale należy wykonać część obciążenia pracą samodzielnie. Kreatory nie obsługują tworzenia klasy specjalnie do tego celu.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Aby utworzyć klasę wywoływania wstępnie zdefiniowanego zapytania (procedury składowanej)

1. Użyj [Kreator użytkownika interfejsu ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Dodaj klasę** do utworzenia klasy zestawu rekordów dla tabeli, która wspiera najbardziej kolumny zwracane przez zapytanie. Dzięki temu można łatwiej rozpocząć pracę.

1. Ręcznie Dodaj elementy członkowskie danych pola dla kolumn wszystkich tabel, które zapytanie zwraca jednak, że Kreator nie utworzono dla Ciebie.

   Na przykład jeśli zapytanie zwraca trzy kolumny z dwóch dodatkowych tabel, należy dodać sześć pól składowych danych (typy danych) do klasy.

1. Ręcznie Dodaj [RFX](../../data/odbc/record-field-exchange-rfx.md) funkcja wywołuje [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcji składowej klasy, jedną odpowiadającą typowi danych każdego typu dodano element członkowski danych pola.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Musisz znać typów danych i kolejność kolumn zwracanych w wyniku zestawu. Kolejność funkcji RFX wywołuje `DoFieldExchange` musi być zgodna z kolejnością kolumny zestawu wyników.

1. Ręcznie Dodaj inicjowania dla nowych elementów członkowskich danych pól w konstruktorze klasy zestawu rekordów.

   Należy również zwiększyć wartość inicjowania [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) element członkowski danych. Kreator zapisuje inicjowania, ale obejmuje tylko elementy członkowskie danych pola, które dodaje się go dla Ciebie. Na przykład:

    ```cpp
    m_nFields += 6;
    ```

   Niektóre typy danych powinna nie można zainicjować w tym miejscu, na przykład `CLongBinary` lub tablice typu byte.

1. Jeśli zapytanie pobiera parametry, należy dodać element członkowski danych parametru dla każdego parametru, wywołanie funkcji RFX dla każdego i Inicjowanie dla każdego.

1. Należy zwiększyć `m_nParams` dla każdego dodano parametr, tak jak `m_nFields` przypadku należy dodać pola w kroku 4 tej procedury. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ręcznie napisać parametry instrukcji SQL w następującej postaci:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   gdzie **WYWOŁANIA** jest kluczowym ODBC **nazwa proc** jest nazwa zapytania jest znany w źródle danych i "?" elementy są symbole zastępcze wartości parametrów, należy dostarczyć do zestawu rekordów w czasie wykonywania (jeśli istnieje) . Poniższy przykład przygotowuje symbolem zastępczym dla jednego parametru:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. W kodzie, który zostanie otwarty zestaw rekordów, ustaw wartości parametrów w zestawie rekordów elementów członkowskich danych, a następnie wywołać `Open` funkcję elementu członkowskiego, przekazując ciąg usługi SQL *lpszSQL* parametru. Lub zamiast tego należy zastąpić ciąg zwracany przez `GetDefaultSQL` funkcja elementu członkowskiego w klasie.

W poniższych przykładach pokazano procedurę wywoływania wstępnie zdefiniowanego zapytania o nazwie `Delinquent_Accts`, która przyjmuje jeden parametr numeru Okręg sprzedaży. Ta kwerenda zwraca trzy kolumny: `Acct_No`, `L_Name`, `Phone`. Są wszystkie kolumny z tabeli Customers.

Poniższy zestaw rekordów określa elementy członkowskie danych pola kolumn zwraca zapytania i parametr dla sprzedaży Dystrykt żądana w czasie wykonywania.

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

Ta deklaracja klasy jest jak Kreator zapisuje, z wyjątkiem `m_lDistParam` ręcznie dodano element członkowski. Inne elementy członkowskie nie są wyświetlane w tym miejscu.

W kolejnym przykładzie pokazano inicjowania dla elementów członkowskich danych w `CDelinquents` konstruktora.

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

Należy pamiętać, inicjowania dla [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) i [m_nparams —](../../mfc/reference/crecordset-class.md#m_nparams). Inicjuje kreatora `m_nFields`; inicjowania `m_nParams`.

W kolejnym przykładzie pokazano funkcje RFX w `CDelinquents::DoFieldExchange`:

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

Oprócz wywołań RFX dla trzech kolumn zwrócone, ten kod zarządza wiązanie parametru, które należy przekazać w czasie wykonywania. Parametr jest kluczem do `Dist_No` kolumny (Dystrykt number).

W kolejnym przykładzie pokazano, jak skonfigurować parametry SQL i jak z niej korzystać, aby otworzyć zestawu rekordów.

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

Ten kod tworzy migawkę, przekazuje on parametr uzyskanymi wcześniej z użytkownika i wywołuje wstępnie zdefiniowanego zapytania. Podczas wykonywania kwerendy, zwraca rekordy określony region sprzedaży. Każdy rekord zawiera kolumny numer konta, nazwiska i numer telefonu klienta.

> [!TIP]
>  Być może chcesz obsługiwać (parametr wyjściowy) wartość zwracana z procedury składowanej. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Zobacz także

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)