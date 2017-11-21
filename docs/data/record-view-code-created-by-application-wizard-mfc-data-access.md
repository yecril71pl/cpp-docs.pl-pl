---
title: "Zapisz kod widok tworzone przez Kreatora aplikacji (dostęp do danych MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9475dd6192eb6bc1abd00e3614c18482be415c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kod widoku rekordu tworzony przez Kreatora aplikacji (dostęp do danych MFC)
[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) Widok pominięć `OnInitialUpdate` i `OnGetRecordset` funkcji elementów członkowskich. Po platformę tworzy ramkę okna dokumentu, a widok, wywołuje `OnInitialUpdate` zainicjować widoku. `OnInitialUpdate`uzyskuje wskaźnik do zestawu rekordów z dokumentu. Wywołania do klasy podstawowej [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcja otwiera zestawu rekordów. Poniższy kod przedstawia ten proces dla `CRecordView`:  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 Po otwarciu zestawu rekordów wybiera rekordy. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) sprawia, że pierwszy rekord bieżącego rekordu i DDX przenosi dane z zestawu rekordów elementy członkowskie danych pola do odpowiednich formantów formularza w widoku. Aby uzyskać więcej informacji na temat RFX, zobacz [wymiany pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md). Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje na temat procesu tworzenia dokumentu/widoku, zobacz [pisać aplikacje dla systemu Windows za pomocą klasy](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
> [!NOTE]
>  Powinien zapewnić użytkownikom końcowym możliwość Odśwież kontrolki widoku rekordu w zestawie. Bez tej możliwości Jeśli użytkownik zmieni wartość formantu na niedozwoloną wartość użytkownik może zostać trwale zablokowana bieżącego rekordu. Aby odświeżyć formantów, należy wywołać `CWnd` funkcji członkowskiej [UpdateData](../mfc/reference/cwnd-class.md#updatedata) z parametrem **FALSE**.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)