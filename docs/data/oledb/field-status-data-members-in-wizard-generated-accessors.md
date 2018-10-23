---
title: Pole elementy członkowskie dotyczące stanu w metodach dostępu generowanych przez kreatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ce3ad819b6e22bfb5c760849e5f3fdf85bd4f7bc
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809099"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Elementy członkowskie dotyczące stanu pola w metodach dostępu generowanych przez kreatora

Gdy używasz OLE DB Kreator konsumenta ATL do utworzenia konsumenta, Kreator generuje element członkowski danych w klasie rekordu użytkownika dla każdego pola, które określisz w mapie kolumny. Każdy element członkowski danych jest typu `DWORD` i zawiera wartość stanu, odpowiadający jej odpowiednich pól.  
  
Na przykład element członkowski danych *m_OwnerID*, Kreator generuje elementu członkowskiego dodatkowe dane dotyczące stanu pola (*dwOwnerIDStatus*) a innym, długość pola (*dwOwnerIDLength*). Generuje mapę kolumny z wpisy COLUMN_ENTRY_LENGTH_STATUS.  
  
Jest to pokazane w poniższym kodzie:  
  
```cpp  
[db_source("insert connection string")]  
[db_command(" \  
   SELECT \  
      Au_ID, \  
      Author, \  
      `Year Born`, \  
      FROM Authors")]  
  
class CAuthors  
{  
public:  
  
   // The following wizard-generated data members contain status   
   // values for the corresponding fields in the column map. You   
   // can use these values to hold NULL values that the database   
   // returns or to hold error information when the compiler returns   
   // errors. See "Field Status Data Members in Wizard-Generated   
   // Accessors" in the Visual C++ documentation for more information   
   // on using these fields.  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
  
   // The following wizard-generated data members contain length  
   // values for the corresponding fields in the column map.  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
  
BEGIN_COLUMN_MAP(CAuthorsAccessor)  
   COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)  
END_COLUMN_MAP()  
  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
      pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
   }  
};  
```  
  
> [!NOTE]
> Jeśli modyfikujesz klasy rekordu użytkownika lub napisać własny konsumenta, zmiennych danych musi występować przed zmienne stanu i długości.  
  
Wartości stanu można użyć na potrzeby debugowania. Jeśli kod wygenerowany przez OLE DB Kreator konsumenta ATL generuje błędy kompilacji, takie jak DB_S_ERRORSOCCURRED lub DB_E_ERRORSOCCURRED, najpierw należy rozważyć bieżących wartości pól elementy członkowskie dotyczące stanu. Te, które mają różną od zera wartości odpowiadają naruszającym kolumn.  
  
Można również użyć wartości stanu, można ustawić wartości NULL dla określonego pola. Pomoże w przypadkach, w których chcesz rozróżnienie wartości pola jako wartość NULL, a nie wartość zero. Jest podjęcie decyzji o wartości NULL, jest prawidłową wartością lub wartością specjalną, i zdecyduj, jak aplikacja powinna obsługiwać go. OLE DB definiuje DBSTATUS_S_ISNULL jako prawidłowy sposób określania ogólnej wartości NULL. Jeśli odbiorca odczytuje dane i ma wartość null, w polu stanu jest równa DBSTATUS_S_ISNULL. Jeśli użytkownik chce, aby ustawić wartość NULL, użytkownik ustawia wartość stanu DBSTATUS_S_ISNULL przed wywołaniem dostawcy.  
  
Następnie otwórz Oledb.h i wyszukaj DBSTATUSENUM. Następnie można dopasować liczbową wartość różną od zera stanu dla DBSTATUSENUM wartości wyliczenia. Jeśli nazwa wyliczenia nie jest wystarczające, aby informujące o tym, czym jest problem, zobacz temat "Status" w sekcji "Powiązanie danych Values" [OLE DB przewodnik](/previous-versions/windows/desktop/ms713643). Ten temat zawiera tabele wartości stanu używany podczas pobierania lub ustawiania danych. Aby uzyskać informacje o wartości długości zobacz temat "Length" w tej samej sekcji.  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>Pobieranie długości lub stan kolumny  

Możesz pobrać długość kolumny zmiennej długości lub stan kolumny (w celu sprawdzania DBSTATUS_S_ISNULL, na przykład):  
  
- Aby uzyskać długości, użyj COLUMN_ENTRY_LENGTH — makro.  
  
- Aby uzyskać stan, użyj COLUMN_ENTRY_STATUS — makro.  
  
- Aby uzyskać zarówno, należy użyć COLUMN_ENTRY_LENGTH_STATUS, jak pokazano poniżej.  
  
```cpp  
class CProducts  
{  
public:  
   char      szName[40];  
   long      nNameLength;  
   DBSTATUS   nNameStatus;  
  
BEGIN_COLUMN_MAP(CProducts)  
// Bind the column to CProducts.m_ProductName.  
// nOrdinal is zero-based, so the column number of m_ProductName is 1.  
   COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CProducts >> product;  
  
product.Open(session, "Product");  

while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
Kiedy używasz `CDynamicAccessor`, długość i stanu są powiązane dla Ciebie automatycznie. Aby pobrać wartości długości i stanu, użyj `GetLength` i `GetStatus` funkcji elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz też  

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)