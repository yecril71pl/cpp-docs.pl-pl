---
title: 'Kontenery kontrolek ActiveX: Łączenie kontrolki ActiveX ze zmienną członkowską | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: ae0cefa518ce44913f5c316a096d221fa9bd41aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433858"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną członkowską

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

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

