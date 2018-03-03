---
title: "Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ecdc146610fe20dcc007d6b1223d7108e1ee595
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie wyjaśniono, jak utworzyć zestaw rekordów klasy dla wstępnie zdefiniowanego zapytania (nazywane również procedury składowanej, jak Microsoft SQL Server).  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli zaimplementowano zbiorcze pobieranie z wiersza proces jest bardzo podobne. Aby poznać różnice między zestawami rekordów, który implementuje zbiorcze pobieranie z wiersza oraz te, które nie zawierają, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Niektóre systemy zarządzania bazami danych (DBMS) pozwalają na tworzenie wstępnie zdefiniowanego zapytania i wywołać go z programów, takich jak funkcja. Zapytanie o nazwie, może przyjmować parametrów i może zwrócić rekordów. Procedury w tym temacie opisano sposób wywołania wstępnie zdefiniowane zapytanie zwraca rekordy (i prawdopodobnie przyjmuje parametry).  
  
 Klasy baz danych nie obsługuje ich aktualizowania wstępnie zdefiniowane zapytania. Różnica między wstępnie zdefiniowanego zapytania migawki i dynamiczny wstępnie zdefiniowanego zapytania nie jest czy można je aktualizować, ale czy zmiany wprowadzone przez innych użytkowników (lub innych zestawów rekordów w programie) są widoczne w twoim zestawie rekordów.  
  
> [!TIP]
>  Zestaw rekordów do wywołania wstępnie zdefiniowanego zapytania, który nie zwraca rekordów nie jest konieczne. Przygotowanie instrukcji SQL, zgodnie z poniższym opisem, ale ją wykonać wywołując `CDatabase` funkcji członkowskiej [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
 Można utworzyć klasy pojedynczy zestaw rekordów do zarządzania wywoływania wstępnie zdefiniowanego zapytania, ale należy wykonać część obciążenia pracą samodzielnie. Kreatorzy nie obsługują tworzenia klasy specjalnie do tego celu.  
  
#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Aby utworzyć klasę wywoływania wstępnie zdefiniowanego zapytania (procedury składowanej)  
  
1.  Użyj [Kreator konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Dodaj klasę** do utworzenia klasy rekordów dla tabeli, która wspiera najbardziej kolumny zwracane przez zapytanie. Dzięki temu można utworzyć.  
  
2.  Ręcznie Dodaj elementy członkowskie danych pola dla kolumn wszystkich tabel, które zapytanie zwraca, ale ten kreator nie może utworzyć dla Ciebie.  
  
     Na przykład jeśli zapytanie zwraca trzy kolumny z dwóch dodatkowych tabel, należy dodać sześciu elementy członkowskie danych pola (typów danych) do klasy.  
  
3.  Ręcznie Dodaj [RFX](../../data/odbc/record-field-exchange-rfx.md) odwołuje się funkcja [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcji członkowskiej klasy, jeden odpowiadającego typowi danych poszczególnych dodany członek pola danych.  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  Należy znać typy danych i ustaw kolejność kolumn zwracanych w wyniku. Kolejność funkcji RFX wywołuje w `DoFieldExchange` musi odpowiadać kolejności kolumn zestawu wyników.  
  
4.  Ręcznie Dodaj inicjowanie dla nowe elementy członkowskie danych pola w konstruktorze klasy zestawu rekordów.  
  
     Należy również zwiększyć wartość inicjowania [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) element członkowski danych. Kreator zapisuje inicjowania, ale obejmuje wyłącznie elementy członkowskie danych pola, które są dodawane automatycznie. Na przykład:  
  
    ```  
    m_nFields += 6;  
    ```  
  
     Niektóre typy danych powinny nie można zainicjować, na przykład `CLongBinary` lub tablice typu byte.  
  
5.  Jeśli zapytanie pobiera parametry, należy dodać element członkowski danych parametru dla każdego parametru, wywołanie funkcji RFX dla każdego i inicjowania dla każdego.  
  
6.  Należy zwiększyć `m_nParams` dla poszczególnych dodanych parametru, tak samo jak `m_nFields` dla dodano pola w kroku 4 tej procedury. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
7.  Ręcznie napisać ciągu instrukcji SQL z następującą postać:  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     gdzie **WYWOŁANIA** jest kluczowym ODBC **nazwa proc** jest nazwa zapytania, ponieważ jest ona znana w źródle danych i "?" elementy są symbole zastępcze wartości parametrów, możesz podać do zestawu rekordów w czasie wykonywania (jeśli istnieje) . Poniższy przykład przygotowuje symbol zastępczy dla jednego parametru:  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  W kodzie, którego kliknięcie spowoduje otwarcie zestawu rekordów, ustaw wartości parametrów w zestawie rekordów elementy członkowskie danych, a następnie wywołać **Otwórz** funkcji członkowskiej, przekazywanie ciągu SQL dla **lpszSQL** parametru. Lub zamiast tego należy zastąpić ciąg zwrócony przez `GetDefaultSQL` funkcji Członkowskich w klasie.  
  
 W poniższych przykładach pokazano procedurę wywoływania wstępnie zdefiniowanego zapytania o nazwie `Delinquent_Accts`, który przyjmuje jeden parametr dla liczbę okręgu sprzedaży. Ta kwerenda zwraca trzy kolumny: `Acct_No`, `L_Name`, `Phone`. Są wszystkie kolumny z tabeli Klienci.  
  
 Następujący zestaw rekordów określa elementy członkowskie danych pola kolumn zwraca zapytania i parametr sprzedaży Dystrykt żądana w czasie wykonywania.  
  
```  
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
  
 Ta deklaracja klasy się kreator zapisuje, z wyjątkiem `m_lDistParam` Członkowskie dodane ręcznie. O innych elementach członkowskich nie są wyświetlane tutaj.  
  
 W kolejnym przykładzie pokazano operacji inicjowania elementów członkowskich danych w `CDelinquents` konstruktora.  
  
```  
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
  
 Należy pamiętać, inicjowanie dla [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) i [m_nparams —](../../mfc/reference/crecordset-class.md#m_nparams). Inicjuje kreatora `m_nFields`; należy zainicjować `m_nParams`.  
  
 W kolejnym przykładzie pokazano funkcje RFX w `CDelinquents::DoFieldExchange`:  
  
```  
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
  
 Oprócz wykonywania wywołań RFX dla trzy kolumny zwracane, ten kod zarządza wiązanie parametru, przebiegu w czasie wykonywania. Parametr jest określonemu `Dist_No` kolumny (liczbę okręgu).  
  
 W kolejnym przykładzie pokazano, jak skonfigurować ciągu SQL i jak z niego korzystać, aby otworzyć zestaw rekordów.  
  
```  
// Construct a CDelinquents recordset object  
CDelinquents rsDel( NULL );  
CString strSQL = "{CALL Delinquent_Accts (?)}"  
// Specify a parameter value (obtained earlier from the user)  
rsDel.m_lDistParam = lDistrict;  
// Open the recordset and run the query  
if( rsDel.Open( CRecordset::snapshot, strSQL ) )  
    // Use the recordset ...  
```  
  
 Ten kod tworzy migawkę, przekazuje on parametr uzyskanymi wcześniej z użytkownika i wywołuje wstępnie zdefiniowanego zapytania. Podczas wykonywania kwerendy, zwraca rejestruje określony region sprzedaży. Każdy rekord zawiera kolumny dla numeru konta, nazwiska i numer telefonu klienta.  
  
> [!TIP]
>  Można obsługiwać (parametr wyjściowy) wartość zwracana z procedury składowanej. Aby uzyskać więcej informacji i przykład zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [Zestaw rekordów: Deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)