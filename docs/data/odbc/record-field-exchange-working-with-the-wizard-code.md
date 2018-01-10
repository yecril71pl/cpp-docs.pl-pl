---
title: "Wymiana pól rekordów: Praca z kodem Kreatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8909a9e933e7b3f1c59fa9ab283706f7a6d1f0c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Wymiana pól rekordów: praca z kodem kreatora
W tym temacie opisano kod który Kreator aplikacji MFC i **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zapisu do obsługi RFX i jak można zmienić tego kodu.  
  
> [!NOTE]
>  Ten temat dotyczy klasy pochodzące od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (RFX zbiorczego) jest zaimplementowana. Zbiorcze RFX jest podobny do RFX. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Podczas tworzenia klasy rekordów przy użyciu Kreatora aplikacji MFC lub **Dodaj klasę**, kreator zapisuje następujące elementy związane z RFX dla tabeli, należy na podstawie źródła danych i opcji kolumny podjąć w Kreatorze:  
  
-   Deklaracje elementy członkowskie danych pola rekordów w klasie zestawu rekordów  
  
-   Zastępowanie`CRecordset::DoFieldExchange`  
  
-   Inicjowanie elementy członkowskie danych pola rekordów w konstruktorze klasy zestawu rekordów  
  
##  <a name="_core_the_field_data_member_declarations"></a>Deklaracje elementu członkowskiego danych pola  
 Kreatorzy zapisu deklaracji klasy zestawu rekordów w pliku .h podobny do następującego dla klasy `CSections`:  
  
```  
class CSections : public CRecordset  
{  
public:  
   CSections(CDatabase* pDatabase = NULL);  
   DECLARE_DYNAMIC(CSections)  
  
// Field/Param Data  
   CString   m_strCourseID;  
   CString   m_strInstructorID;  
   CString   m_strRoomNo;  
   CString   m_strSchedule;  
   CString   m_strSectionNo;  
  
// Overrides  
   // Wizard generated virtual function overrides  
   protected:  
   virtual CString GetDefaultConnect();  // Default connection string  
   virtual CString GetDefaultSQL();      // Default SQL for Recordset  
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support  
  
// Implementation  
#ifdef _DEBUG  
   virtual void AssertValid() const;  
   virtual void Dump(CDumpContext& dc) const;  
#endif  
  
};  
```  
  
 Jeśli dodasz elementy członkowskie danych parametru lub nowe elementy członkowskie danych pola powiązane samodzielnie, należy je dodać po nich generowane przez kreatora.  
  
 Ponadto powiadomienia zastępujący kreatora `DoFieldExchange` funkcji członkowskiej klasy `CRecordset`.  
  
##  <a name="_core_the_dofieldexchange_override"></a>DoFieldExchange zastąpienia  

 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) jest centralnym RFX. Wywołania framework `DoFieldExchange` dowolnej chwili należy przenieść dane ze źródła danych do zestawu rekordów lub z zestawu rekordów do źródła danych. `DoFieldExchange`również obsługuje uzyskiwania informacji na temat pól członków danych za pośrednictwem [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) i [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) funkcji elementów członkowskich.  
  
 Następujące `DoFieldExchange` jest zastąpienie `CSections` klasy. Kreator zapisuje funkcji w pliku .cpp klasy zestawu rekordów.  
  
```  
void CSections::DoFieldExchange(CFieldExchange* pFX)  
{  
   pFX->SetFieldType(CFieldExchange::outputColumn);  
   RFX_Text(pFX, "CourseID", m_strCourseID);  
   RFX_Text(pFX, "InstructorID", m_strInstructorID);  
   RFX_Text(pFX, "RoomNo", m_strRoomNo);  
   RFX_Text(pFX, "Schedule", m_strSchedule);  
   RFX_Text(pFX, "SectionNo", m_strSectionNo);  
}  
```  
  
 Zwróć uwagę, następujące funkcje kluczowych funkcji:  
  
-   Ta sekcja funkcja jest wywoływana mapowanie pola.  
  
-   Wywołanie `CFieldExchange::SetFieldType`, za pomocą `pFX` wskaźnika. To wywołanie określa, że wszystkie funkcje RFX wymaga na końcu `DoFieldExchange` lub następne wywołanie `SetFieldType` kolumn danych wyjściowych. Aby uzyskać więcej informacji, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
-   Wiele wywołań `RFX_Text` funkcji globalnej — po jednym dla każdego elementu członkowskiego danych pola (wszystkie są `CString` zmiennych w przykładzie). Te wywołania Określ relację między nazwę kolumny w źródle danych i element członkowski danych pola. Funkcje RFX do transferu danych rzeczywistych. Biblioteka klas udostępnia funkcje RFX wszystkie typy danych. Aby uzyskać więcej informacji na temat funkcji RFX, zobacz [wymiana pól rekordów: używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).  
  
    > [!NOTE]
    >  Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością wywołań funkcji RFX w `DoFieldExchange`.  
  
-   `pFX` Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiekt, który przekazuje platformę, gdy wywołuje `DoFieldExchange`. `CFieldExchange` Operacji określa obiekt który `DoFieldExchange` jest wykonanie kierunek transferu i inne informacje o kontekście.  
  
##  <a name="_core_the_recordset_constructor"></a>Konstruktor zestawu rekordów  
 Konstruktor zestawu rekordów, który zapisu kreatorów zawiera dwie czynności związane z RFX:  
  
-   Inicjowanie dla każdego elementu członkowskiego danych pola  
  
-   Inicjowanie dla [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) element członkowski danych, która zawiera liczbę elementy członkowskie danych pola  
  
 Konstruktor `CSections` przykład zestawu rekordów wygląda następująco:  
  
```  
CSections::CSections(CDatabase* pdb)  
   : CRecordset(pdb)  
{  
   m_strCourseID = "";  
   m_strInstructorID = "";  
   m_strRoomNo = "";  
   m_strSchedule = "";  
   m_strSectionNo = "";  
   m_nFields = 5;  
}  
```  
  
> [!NOTE]
>  Jeśli dodasz wszystkie elementy członkowskie danych pola ręcznie, jak może dynamicznie w przypadku powiązania nowe kolumny, należy zwiększyć `m_nFields`. To zrobić przez dołączenie kolejny wiersz kodu, takich jak:  
  
```  
m_nFields += 3;  
```  

 To jest kod dodaje trzy nowe pola. Jeśli dodasz wszystkie elementy członkowskie danych parametru, należy zainicjować [m_nparams —](../../mfc/reference/crecordset-class.md#m_nparams) element członkowski danych, która zawiera liczbę elementy członkowskie danych parametru. Umieść `m_nParams` inicjowania poza nawiasów.  

  
## <a name="see-also"></a>Zobacz też  
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)