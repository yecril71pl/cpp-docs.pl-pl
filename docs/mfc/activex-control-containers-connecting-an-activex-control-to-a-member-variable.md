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
ms.openlocfilehash: 87cb560a1054a912a4e8574cfe2dee74d5e61fe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625133"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną członkowską

Najprostszym sposobem uzyskania dostępu do kontrolki ActiveX z poziomu jej aplikacji kontenera kontrolek jest skojarzenie kontrolki ActiveX ze zmienną członkowską klasy okna dialogowego, która będzie zawierać formant.

> [!NOTE]
> Nie jest to jedyna metoda uzyskiwania dostępu do osadzonego formantu z klasy kontenera, ale na potrzeby tego artykułu jest to wystarczające.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Dodawanie zmiennej członkowskiej do klasy okna dialogowego

1. W Widok klasy kliknij prawym przyciskiem myszy główną klasę okna dialogowego, aby otworzyć menu skrótów. Na przykład `CContainerDlg`.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie **Dodaj zmienną**.

1. W Kreatorze dodawania zmiennej członkowskiej kliknij pozycję **sterowanie zmienna**.

1. W polu listy **Identyfikator formantu** wybierz identyfikator kontrolki osadzonej kontrolki ActiveX. Na przykład `IDC_CIRCCTRL1`.

1. W polu **Nazwa zmiennej** wprowadź nazwę.

   Na przykład *m_circctl*.

1. Kliknij przycisk **Zakończ** , aby zaakceptować wybrane opcje i zakończyć pracę Kreatora dodawania zmiennej członkowskiej.

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](activex-control-containers.md)
