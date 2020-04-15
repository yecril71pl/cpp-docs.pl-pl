---
title: 'Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną członkowską'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: 620a9ec58b3a5a8fcdac63626b81fbc4620de399
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371616"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną członkowską

Najprostszym sposobem uzyskania dostępu do formantu ActiveX z poziomu jego aplikacji kontenera sterowania jest skojarzenie formantu ActiveX ze zmienną członkowną klasy okna dialogowego, która będzie zawierać formant.

> [!NOTE]
> Nie jest to jedyny sposób, aby uzyskać dostęp do osadzonego formantu z poziomu klasy kontenera, ale na potrzeby tego artykułu jest wystarczające.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Dodawanie zmiennej elementu członkowskiego do klasy okna dialogowego

1. W widoku klasy kliknij prawym przyciskiem myszy główną klasę okna dialogowego, aby otworzyć menu skrótów. Na przykład `CContainerDlg`.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie **dodaj zmienną**.

1. W Kreatorze dodawania zmiennej elementu członkowskiego kliknij pozycję **Zmienna formantu**.

1. W polu listy **Identyfikator sterowania** wybierz identyfikator formantu osadzonego formantu ActiveX. Na przykład `IDC_CIRCCTRL1`.

1. W polu **Nazwa zmiennej** wprowadź nazwę.

   Na przykład *m_circctl*.

1. Kliknij **przycisk Zakończ,** aby zaakceptować wybory i zakończyć pracę Kreatora dodawania zmiennej elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
