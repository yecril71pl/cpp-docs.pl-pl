---
title: Kod widoku rekordu utworzony przez Kreatora aplikacji (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69481299980329b98e378f02e090670fa3d7ece2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376021"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kod widoku rekordu utworzony przez Kreatora aplikacji (MFC Data Access)

[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) zastępuje funkcje `OnInitialUpdate` widoku `OnGetRecordset` i elementu członkowskiego. Po utworzenie struktury okna ramki, dokumentu i `OnInitialUpdate` widoku, wywołuje zainicjowanie widoku. `OnInitialUpdate`uzyskuje wskaźnik do pliku recordset z dokumentu. Wywołanie klasy podstawowej [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcja otwiera zestawie rekordów. Poniższy kod przedstawia ten `CRecordView`proces dla:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Po otwarciu pliku records wybiera rekordy. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) sprawia, że pierwszy rekord bieżący rekord i DDX przenosi dane z elementów członkowskich danych pola zestawu rekordów do odpowiednich formantów formularza w widoku. Aby uzyskać więcej informacji na temat RFX, zobacz [Wymiana pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md). Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje o procesie tworzenia dokumentu/widoku, zobacz [Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
> Należy dać użytkownikom końcowym możliwość odświeżenia formantów widoku rekordów z akusety rekordów. Bez tej możliwości, jeśli użytkownik zmieni wartość formantu na wartość niedozwolone, użytkownik może być trwale zatrzymany na bieżącym rekordzie. Aby odświeżyć formanty, należy wywołać funkcję `CWnd` członkowską [UpdateData](../mfc/reference/cwnd-class.md#updatedata) z parametrem FALSE.

## <a name="see-also"></a>Zobacz też

[Korzystanie z widoku rekordu](../data/using-a-record-view-mfc-data-access.md)
