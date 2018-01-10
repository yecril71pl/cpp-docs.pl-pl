---
title: "Kontenery formantów ActiveX: Łączenie formantu ActiveX ze zmienną członkowską | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2248dd68b0ecc7471899552bcb7b0394f3f9f363
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

