---
title: Pola w metodach dostępu generowanych przez kreatora, elementy członkowskie dotyczących stanu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3f1017c3decacfee223f0e0f89267b192208fe7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Elementy członkowskie dotyczące stanu pola w metodach dostępu generowanych przez kreatora
Użycie do utworzenia konsumenta OLE DB Kreator konsumenta ATL, Kreator generuje element członkowski danych klasy rekordu użytkownika, dla każdego pola, które określisz na mapie kolumny. Każdy element członkowski danych jest typu `DWORD` i zawiera wartość stanu, odpowiadający jej odpowiednie pola.  
  
 Na przykład dla elementu członkowskiego danych *m_OwnerID*, Kreator generuje elementu członkowskiego dodatkowe dane dotyczące stanu pola (*dwOwnerIDStatus*) a innym długość pola (*dwOwnerIDLength*). Generuje on również mapowanie kolumn o `COLUMN_ENTRY_LENGTH_STATUS` wpisów.  
  
 Przedstawiono to w poniższym kodzie:  
  
```  
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
>  Modyfikowanie klasy rekordów użytkowników lub napisać własny konsumenta, zmiennych danych musi występować przed zmienne stanu i długości.  
  
 Można użyć wartości stanu na potrzeby debugowania. Jeśli kod wygenerowany przez OLE DB Kreator konsumenta ATL generuje błędy kompilacji, takie jak **DB_S_ERRORSOCCURRED** lub **DB_E_ERRORSOCCURRED**, najpierw należy zwrócić uwagę na bieżące wartości stan pola elementy członkowskie danych. Te, które mają niezerowe wartości odpowiadają kolumnom ataku.  
  
 Umożliwia także wartości stanu można ustawić wartości NULL dla określonego pola. Pomoże w przypadkach, w których chcesz odróżnić wartość pola wartość NULL, a nie zero. Jest można zdecydować, czy wartość NULL jest nieprawidłowa wartość lub wartość specjalne oraz zdecydować, jak aplikacja powinna obsługiwać go. Definiuje OLE DB **DBSTATUS_S_ISNULL** jako poprawne sposób określania ogólnego wartość NULL. Jeśli użytkownik odczytuje dane i ma wartość null, w polu stanu ma ustawioną **DBSTATUS_S_ISNULL**. Jeśli użytkownik chce ustawić wartości NULL, konsumenta ustawia wartość stanu **DBSTATUS_S_ISNULL** przed wywołaniem dostawcy.  
  
 Następnie otwórz Oledb.h i wyszukaj **DBSTATUSENUM**. Następnie można dopasować liczbowa wartość niezerową stanu przed **DBSTATUSENUM** wartości wyliczenia. Jeśli nazwa wyliczenia nie wystarcza do informujące o tym, co jest nieprawidłowe, zobacz temat "Status" w sekcji "Powiązania danych wartości" [OLE DB przewodnik](http://go.microsoft.com/fwlink/p/?linkid=121548). Ten temat zawiera tabele używane podczas pobierania lub ustawiania danych wartości stanu. Aby uzyskać informacje o wartości długości zobacz temat "Length" w tej samej sekcji.  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>Pobieranie długości lub stan kolumny  
 Można pobrać długość kolumny o zmiennej długości, a także stan kolumny (Aby wyszukać **DBSTATUS_S_ISNULL**, na przykład):  
  
-   Aby pobrać długości, należy użyć `COLUMN_ENTRY_LENGTH` makra.  
  
-   Aby uzyskać stan, użyj `COLUMN_ENTRY_STATUS` makra.  
  
-   Aby uzyskać zarówno, należy użyć `COLUMN_ENTRY_LENGTH_STATUS`, jak pokazano poniżej.  
  
```  
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
  
 Jeśli używasz `CDynamicAccessor`, długość i stan są powiązane można automatycznie. Aby pobrać wartości długości i stanu, należy użyć `GetLength` i **GetStatus** funkcji elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)