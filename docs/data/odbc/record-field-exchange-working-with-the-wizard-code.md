---
title: 'Wymiana pól rekordów: Praca z kodem Kreatora'
ms.date: 11/04/2016
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
ms.openlocfilehash: 82f0d946cac3429150250e2df5d1bfd674ec30ee
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041296"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Wymiana pól rekordów: Praca z kodem Kreatora

W tym temacie opisano kod, Kreator aplikacji MFC i **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zapisu do obsługi RFX i jak możesz chcieć zmienić kod.

> [!NOTE]
>  Ten temat dotyczy klasy pochodne `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (zbiorcze RFX) jest zaimplementowana. Zbiorcze RFX przypomina RFX. Aby poznać różnice, zobacz [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Po utworzeniu klasy zestawu rekordów za pomocą Kreatora aplikacji MFC lub **Dodaj klasę**, kreator zapisuje następujące elementy związane z RFX dla użytkownika, na podstawie źródła danych tabeli, a wybór kolumny wprowadzić w Kreatorze:

- Deklaracje elementy członkowskie danych pola zestawu rekordów w klasie zestawu rekordów

- Zastąpieniu obiektu `CRecordset::DoFieldExchange`

- Inicjowanie elementy członkowskie danych pola zestawu rekordów w konstruktorze klasy zestawu rekordów

##  <a name="_core_the_field_data_member_declarations"></a> Deklaracje członków danych pola

Kreatorzy zapisu deklarację klasy zestawu rekordów w pliku .h, który jest podobny do następującego dla klasy `CSections`:

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

Jeśli dodasz elementy członkowskie danych parametru lub nowe elementy członkowskie pola, które można powiązać samodzielnie, należy je dodać po nich generowane przez kreatora.

Ponadto w przypadku Zauważ, że kreator zastępuje `DoFieldExchange` funkcji składowej klasy typu `CRecordset`.

##  <a name="_core_the_dofieldexchange_override"></a> Dofieldexchange — zastąpienie

[Dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) jest sercem RFX. Struktura wywołuje `DoFieldExchange` wszelkie czas potrzebny do przenoszenia danych ze źródła danych do zestawu rekordów lub z zestawu rekordów do źródła danych. `DoFieldExchange` również obsługuje uzyskiwania informacji na temat pól składowych danych za pośrednictwem [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) i [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) funkcji elementów członkowskich.

Następujące `DoFieldExchange` jest zastąpienie `CSections` klasy. Kreator zapisuje funkcji w pliku .cpp dla swojej klasy zestawu rekordów.

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

Zwróć uwagę, następujące kluczowe funkcje tej funkcji:

- Ta sekcja funkcja jest wywoływana mapowanie pola.

- Wywołanie `CFieldExchange::SetFieldType`za pośrednictwem `pFX` wskaźnika. To wywołanie określa, że wszystkie funkcje RFX wywołuje na końcu `DoFieldExchange` lub następnym wywołaniu `SetFieldType` kolumn w danych wyjściowych. Aby uzyskać więcej informacji, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Kilka wywołań `RFX_Text` funkcja globalna — jednym w każdym polu element członkowski danych (wszystkie są `CString` zmiennych w przykładzie). Te wywołania Określ relację między nazwę kolumny w źródle danych i element członkowski danych pola. Funkcje RFX do transferu danych rzeczywistych. Biblioteka klas dostarcza funkcje RFX wszystkie popularne typy danych. Aby uzyskać więcej informacji na temat funkcji RFX zobacz [wymiana pól rekordów: Używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  Kolejność kolumn w zestawie wyników musi być zgodna z kolejnością wywołań funkcji RFX w `DoFieldExchange`.

- `pFX` Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiekt, który przekazuje platformę, gdy wywołuje `DoFieldExchange`. `CFieldExchange` Obiektu określa operację, `DoFieldExchange` jest wykonanie kierunek transferu i innymi informacjami kontekstu.

##  <a name="_core_the_recordset_constructor"></a> Recordset Constructor

Konstruktor zestawu rekordów, który kreatorów zapisu zawiera dwie czynności związane z RFX:

- Inicjowanie dla każdego elementu członkowskiego danych pola

- Inicjowanie [m_nfields —](../../mfc/reference/crecordset-class.md#m_nfields) element członkowski danych, która zawiera liczbę elementów członkowskich danych pola

Konstruktor `CSections` przykład zestawu rekordów wygląda następująco:

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
>  Jeśli dodasz żadnych składowych danych pola ręcznie, jak to się dzieje, jeśli dynamicznie powiązana nowych kolumn, należy zwiększyć `m_nFields`. To zrobić, dodając innego wiersza kodu, takich jak:

```cpp
m_nFields += 3;
```

Jest to kod dodaje trzy nowe pola. Jeśli dodasz wszystkie elementy członkowskie danych parametru, należy zainicjować [m_nparams —](../../mfc/reference/crecordset-class.md#m_nparams) element członkowski danych, która zawiera liczbę elementy członkowskie danych parametru. Umieść `m_nParams` inicjowania poza nawiasy kwadratowe.

## <a name="see-also"></a>Zobacz także

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)