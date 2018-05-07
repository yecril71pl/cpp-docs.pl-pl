---
title: 'Kontenery formantów ActiveX: Łączenie formantu ActiveX ze zmienną członkowską | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a2b6a5ab17db7b512f1f44d2eda68169d71645
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną członkowską
Najłatwiejszym sposobem na dostęp do formantu ActiveX w swojej aplikacji kontenera formantów jest do skojarzenia z formantu ActiveX ze zmienną członkowską klasy okna dialogowego, który będzie zawierać formant.  
  
> [!NOTE]
>  To nie jest jedynym sposobem, aby uzyskać dostęp do osadzonego formantu z wewnątrz klasy kontenera, ale na potrzeby tego artykułu jest wystarczająca.  
  
### <a name="adding-a-member-variable-to-the-dialog-class"></a>Dodawanie zmienną członkowską do klasy okien dialogowych  
  
1.  Z widoku klasy kliknij prawym przyciskiem myszy klasy głównym oknie dialogowym, aby otworzyć menu skrótów. Na przykład `CContainerDlg`.  
  
2.  W menu skrótów kliknij **Dodaj** , a następnie **Dodaj zmienną**.  
  
3.  W Kreatorze dodawania zmiennej elementu członkowskiego kliknij **zmienna sterująca**.  
  
4.  W **Identyfikatora formantu** pola listy, wybierz identyfikator formantu osadzonego formantu ActiveX. Na przykład `IDC_CIRCCTRL1`.  
  
5.  W **nazwa zmiennej** wprowadź nazwę.  
  
     Na przykład `m_circctl`.  
  
6.  Kliknij przycisk **Zakończ** aby zaakceptować wybrane opcje i zamknąć Dodaj kreatora zmiennej elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

