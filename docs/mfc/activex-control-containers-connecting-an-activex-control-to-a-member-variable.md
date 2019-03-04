---
title: 'Kontenery kontrolek ActiveX: Łączenie kontrolki ActiveX ze zmienną członkowską'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: c6bc063875f2a31c582c9de32e24e7dfbc7826c9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279942"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontenery kontrolek ActiveX: Łączenie kontrolki ActiveX ze zmienną członkowską

Jest najprostszym sposobem na dostęp do formantu ActiveX w swojej aplikacji kontenera kontrolek do skojarzenia kontrolki ActiveX ze zmienną składową klasy okna dialogowego, który będzie zawierać formantu.

> [!NOTE]
>  Nie jest jedynym sposobem, aby uzyskać dostęp do osadzonego formantu z w obrębie klasy kontenera, ale na potrzeby tego artykułu jest wystarczająca.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Dodawanie zmiennej członkowskiej do klasy okien dialogowych

1. W widoku klas kliknij prawym przyciskiem myszy klasę głównym oknie dialogowym, aby otworzyć menu skrótów. Na przykład `CContainerDlg`.

1. W menu skrótów kliknij **Dodaj** i następnie **Dodaj zmienną**.

1. W Kreatorze dodawania zmiennej składowej kliknij **zmienna sterująca**.

1. W **identyfikator formantu** pola listy, wybierz identyfikator formantu osadzonego formantu ActiveX. Na przykład `IDC_CIRCCTRL1`.

1. W **nazwa zmiennej** wprowadź nazwę.

   Na przykład *m_circctl*.

1. Kliknij przycisk **Zakończ** aby zaakceptować wybór i zamknąć okno Dodaj kreatora zmiennej elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
