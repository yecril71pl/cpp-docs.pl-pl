---
title: 'Wymiana pól rekordów: praca z kodem kreatora'
ms.date: 05/09/2019
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
ms.openlocfilehash: 8e42fc9da672ca4ef97e775776935650ab7f545a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367116"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Wymiana pól rekordów: praca z kodem kreatora

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

W tym temacie wyjaśniono kod, który Kreator aplikacji MFC i **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta ODBC MFC)](../../mfc/reference/adding-an-mfc-odbc-consumer.md)zapis do obsługi RFX i jak można zmienić ten kod.

> [!NOTE]
> Ten temat ma zastosowanie do `CRecordset` klas pochodzących z których pobieranie wiersza zbiorczego nie została zaimplementowana. W przypadku pobierania wierszy zbiorczych zaimplementowana jest zbiorcza wymiana pól rekordów (Bulk RFX). Zbiorczy RFX jest podobny do RFX. Aby zrozumieć różnice, zobacz [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Podczas tworzenia klasy zestawów rekordów za pomocą Kreatora aplikacji MFC lub **Klasy dodawania**kreator zapisuje następujące elementy związane z RFX na podstawie opcji źródła danych, tabeli i kolumn dokonywanych w kreatorze:

- Deklaracje elementów członkowskich danych pola zbioru rekordów w klasie zestaw rekordów

- Zastąpienie`CRecordset::DoFieldExchange`

- Inicjowanie elementów członkowskich danych pól zestawów rekordów w konstruktorze klasy zestaw rekordów

## <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a>Deklaracje elementów członkowskich danych pól

Kreatorzy zapisują deklarację klasy pliku recordset w pliku .h, która przypomina następującą dla klasy: `CSections`

```cpp
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

Jeśli dodasz elementy członkowskie danych parametrów lub nowe elementy członkowskie danych pola, które wiążą się samodzielnie, dodaj je po tych generowanych przez kreatora.

Należy również zauważyć, że kreator `DoFieldExchange` zastępuje funkcję `CRecordset`elementu członkowskiego klasy .

## <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a>Zastępowanie dofieldexchange

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) jest sercem RFX. Struktura wywołuje `DoFieldExchange` za każdym razem, gdy musi przenieść dane ze źródła danych do pliku recordset lub z zestawu rekordów do źródła danych. `DoFieldExchange`obsługuje również uzyskiwanie informacji o elementach członkowskich danych pól za pośrednictwem funkcji członkowskich [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) i [IsFieldNull.](../../mfc/reference/crecordset-class.md#isfieldnull)

Następujące `DoFieldExchange` zastąpienie jest dla `CSections` klasy. Kreator zapisuje funkcję w pliku cpp dla klasy pliku recordset.

```cpp
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

Zwróć uwagę na następujące kluczowe cechy funkcji:

- Ta sekcja funkcji jest nazywana mapą pola.

- Wywołanie `CFieldExchange::SetFieldType`, przez `pFX` wskaźnik. To wywołanie określa, że wszystkie wywołania funkcji `DoFieldExchange` RFX `SetFieldType` do końca lub następnego wywołania są kolumnami wyjściowymi. Aby uzyskać więcej informacji, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Kilka wywołań `RFX_Text` funkcji globalnej — jeden na element `CString` członkowski danych pola (z których wszystkie są zmiennymi w przykładzie). Te wywołania określają relację między nazwą kolumny w źródle danych a elementem członkowskim danych pola. Funkcje RFX wykonują rzeczywisty transfer danych. Biblioteka klas dostarcza funkcje RFX dla wszystkich typowych typów danych. Aby uzyskać więcej informacji na temat funkcji RFX, zobacz [Wymiana pól rekordu: Korzystanie z funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością wywołań funkcji RFX w `DoFieldExchange`.

- Wskaźnik `pFX` do [obiektu CFieldExchange,](../../mfc/reference/cfieldexchange-class.md) który przekazuje `DoFieldExchange`framework podczas wywołania . Obiekt `CFieldExchange` określa operację, `DoFieldExchange` która ma być wykonywane, kierunek transferu i inne informacje kontekstowe.

## <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a>Konstruktor nastawy rekordów

Konstruktor modułu recordset, który zapisują kreatorzy, zawiera dwie rzeczy związane z RFX:

- Inicjowanie dla każdego elementu członkowskiego danych pola

- Inicjowanie [elementu](../../mfc/reference/crecordset-class.md#m_nfields) członkowskiego m_nFields danych, który zawiera liczbę elementów członkowskich danych pola

Konstruktor dla `CSections` przykładu recordset wygląda następująco:

```cpp
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
> Jeśli dodasz elementy członkowskie danych pól ręcznie, tak jak w przypadku dynamicznego `m_nFields`powiększenia nowych kolumn, należy zwiększyć program . Aby to zrobić, dołączając inny wiersz kodu, taki jak:

```cpp
m_nFields += 3;
```

Jest to kod dodawania trzech nowych pól. Jeśli dodasz żadnych elementów członkowskich danych parametrów, należy zainicjować element członkowski [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) danych, który zawiera liczbę elementów członkowskich danych parametrów. Umieść `m_nParams` inicjalizację poza nawiasami.

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
