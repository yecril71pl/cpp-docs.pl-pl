---
title: Kod widoku rekordu tworzony przez Kreatora aplikacji (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: e25ca9cad1390dd11ab7328ffefed31badf6fc0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152686"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kod widoku rekordu tworzony przez Kreatora aplikacji (dostęp do danych MFC)

[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) Widok pominięć `OnInitialUpdate` i `OnGetRecordset` funkcji elementów członkowskich. Po utworzeniu Struktura ramki okna, dokument i widok, wywołuje `OnInitialUpdate` zainicjować widoku. `OnInitialUpdate` uzyskuje wskaźnik do zestawu rekordów z dokumentu. Wywołania do klasy bazowej [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcji zostanie otwarty zestaw rekordów. Poniższy kod ilustruje ten proces dla `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Po otwarciu zestawu rekordów wybiera rekordy. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) sprawia, że pierwszy rekord bieżący rekord oraz DDX przenosi dane z elementy członkowskie danych pola w zestawie rekordów do odpowiednich formantów formularza w widoku. Aby uzyskać więcej informacji na temat RFX zobacz [wymiany pól rekordu (RFX)](../data/odbc/record-field-exchange-rfx.md). Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje na temat procesu tworzenia dokumentu/widoku, zobacz [używanie klas do pisania aplikacji dla Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
>  Powinien zapewnić użytkownikom końcowym możliwość odświeżania kontrolki widoku rekordu w zestawie. Bez tej możliwości Jeśli użytkownik zmieni wartość formantu na niedozwoloną wartość użytkownika można trwale utknąć w bieżącym rekordzie. Aby odświeżyć kontrolek, należy wywołać `CWnd` funkcja elementu członkowskiego [updatedata —](../mfc/reference/cwnd-class.md#updatedata) z parametrem wartość FALSE.

## <a name="see-also"></a>Zobacz także

[Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)