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
ms.openlocfilehash: f9618f25d738c092ab1818ef7c4ea52928e2ea60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367039"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak utworzyć klasę akwizycji dla wstępnie zdefiniowanej kwerendy (czasami nazywanej procedurą składowaną, jak w programie Microsoft SQL Server).

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli pobieranie wiersza zbiorczego jest zaimplementowane, proces jest bardzo podobny. Aby zrozumieć różnice między zestawy rekordów, które implementują pobieranie wierszy luzem i tych, które nie, zobacz [Recordset: Pobieranie rekordów luzem (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Niektóre systemy zarządzania bazami danych (DBMSs) umożliwiają utworzenie wstępnie zdefiniowanej kwerendy i wywołanie jej z programów, takich jak funkcja. Kwerenda ma nazwę, może przyjmować parametry i może zwracać rekordy. Procedura opisana w tym temacie opisano sposób wywoływania wstępnie zdefiniowanej kwerendy, która zwraca rekordy (i być może przyjmuje parametry).

Klasy bazy danych nie obsługują aktualizowania wstępnie zdefiniowanych zapytań. Różnica między wstępnie zdefiniowaną kwerendą migawką a wstępnie zdefiniowaną kwerendą dynasetową nie jest możliwość aktualizacji, ale to, czy zmiany wprowadzone przez innych użytkowników (lub inne zestawy rekordów w programie) są widoczne w zestawie rekordów.

> [!TIP]
> Nie potrzebujesz pliku recordset do wywołania wstępnie zdefiniowanej kwerendy, która nie zwraca rekordów. Przygotuj instrukcję SQL, jak opisano poniżej, `CDatabase` ale wykonaj ją, wywołując funkcję elementu członkowskiego [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Można utworzyć pojedynczą klasę pliku recordset, aby zarządzać wywoływaniem wstępnie zdefiniowanej kwerendy, ale niektóre prace należy wykonać samodzielnie. Kreatorzy nie obsługują tworzenia klasy specjalnie w tym celu.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Aby utworzyć klasę wywoływania wstępnie zdefiniowanej kwerendy (procedura składowana)

1. Użyj [Kreatora konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **dodaj klasę,** aby utworzyć klasę tablicy rekordów dla tabeli, która przyczynia się do większości kolumn zwróconych przez kwerendę. To daje przewagę.

1. Ręcznie dodaj elementy członkowskie danych pól dla wszystkich kolumn tabel zwracanych przez kwerendę, ale kreator nie został utworzony dla Ciebie.

   Na przykład jeśli kwerenda zwraca trzy kolumny z dwóch dodatkowych tabel, dodaj sześć elementów członkowskich danych pola (odpowiednich typów danych) do klasy.

1. Ręcznie dodaj wywołania funkcji [RFX](../../data/odbc/record-field-exchange-rfx.md) w funkcji elementu członkowskiego [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) klasy, która odpowiada typowi danych każdego dodanego elementu członkowskiego danych pola.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Musisz znać typy danych i kolejność kolumn zwracanych w zestawie wyników. Kolejność wywołań funkcji RFX `DoFieldExchange` musi być zgodna z kolejnością kolumn zestawu wyników.

1. Ręcznie dodaj inicjalizowania dla nowych elementów członkowskich danych pola w konstruktorze klasy zestaw rekordów.

   Należy również zwiększać wartość inicjowania dla [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) elementu członkowskiego danych. Kreator zapisuje inicjalizację, ale obejmuje tylko elementy członkowskie danych pola, które dodaje dla Ciebie. Przykład:

    ```cpp
    m_nFields += 6;
    ```

   Niektóre typy danych nie powinny być `CLongBinary` inicjowane w tym miejscu, na przykład lub tablice bajtowe.

1. Jeśli kwerenda przyjmuje parametry, dodaj element członkowski danych parametru dla każdego parametru, wywołanie funkcji RFX dla każdego z nich i inicjowanie dla każdego.

1. Należy przyrost dla `m_nParams` każdego dodanego parametru, tak jak `m_nFields` w przypadku dodanych pól w kroku 4 tej procedury. Aby uzyskać więcej informacji, zobacz [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ręcznie napisz ciąg instrukcji SQL z następującym formularzem:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   gdzie **CALL** jest słowem kluczowym ODBC, **nazwa proc** jest nazwą kwerendy, jak jest znana w źródle danych, a elementy "?" są symbolami zastępczymi dla wartości parametrów podanych do zestawu rekordów w czasie wykonywania (jeśli istnieją). Poniższy przykład przygotowuje symbol zastępczy dla jednego parametru:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. W kodzie, który otwiera zestaw rekordów, ustaw wartości elementów członkowskich `Open` danych parametrów zestawu rekordów, a następnie wywołaj funkcję elementu członkowskiego, przekazując ciąg SQL dla parametru *lpszSQL.* Lub zamiast tego zastąp `GetDefaultSQL` ciąg zwrócony przez funkcję elementu członkowskiego w klasie.

Poniższe przykłady przedstawiają procedurę wywoływania wstępnie zdefiniowanej `Delinquent_Accts`kwerendy o nazwie , która przyjmuje jeden parametr dla numeru okręgu sprzedaży. Ta kwerenda zwraca `Acct_No`trzy `L_Name` `Phone`kolumny: , , . Wszystkie kolumny są z tabeli Klienci.

Poniższy zestaw rekordów określa elementy członkowskie danych pól dla kolumn zwraca zapytanie i parametr dla numeru okręgu sprzedaży żądanego w czasie wykonywania.

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

Ta deklaracja klasy jest jak kreator pisze `m_lDistParam` go, z wyjątkiem elementu członkowskiego dodane ręcznie. Inne elementy członkowskie nie są wyświetlane w tym miejscu.

W następnym przykładzie przedstawiono inicjalizowania dla elementów członkowskich danych w konstruktorze. `CDelinquents`

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

Zanotuj inicjalizowania [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) i [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Kreator inicjuje `m_nFields`; zainicjować `m_nParams`.

W następnym przykładzie przedstawiono `CDelinquents::DoFieldExchange`funkcje RFX w :

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

Oprócz podejmowania RFX wywołania dla trzech zwróconych kolumn, ten kod zarządza powiązanie parametru, który przekazujesz w czasie wykonywania. Parametr jest kluczem `Dist_No` do kolumny (numer okręgu).

W następnym przykładzie pokazano, jak skonfigurować ciąg SQL i jak go używać do otwierania zestawu rekordów.

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

Ten kod tworzy migawkę, przekazuje jej parametr uzyskany wcześniej od użytkownika i wywołuje wstępnie zdefiniowaną kwerendę. Po uruchomieniu kwerendy zwraca rekordy dla określonego okręgu sprzedaży. Każdy rekord zawiera kolumny numeru konta, nazwiska klienta i numeru telefonu klienta.

> [!TIP]
> Można obsługiwać wartość zwracaną (parametr wyjściowy) z procedury składowanej. Aby uzyskać więcej informacji i przykład, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
