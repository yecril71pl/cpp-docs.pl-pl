---
title: CTreeCtrl vs. CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 7c78dfa9920c913fdbedb009c5a6f275a3e3e273
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445233"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView

MFC udostępnia dwie klasy, które hermetyzują formanty drzewa: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) i [CTreeView](../mfc/reference/ctreeview-class.md). Każda klasa jest przydatna w różnych sytuacjach.

Użyj `CTreeCtrl`, gdy potrzebujesz prostej kontrolki okna podrzędnego; na przykład w oknie dialogowym. W szczególności warto używać `CTreeCtrl`, jeśli w oknie są inne kontrolki podrzędne, jak w przypadku typowego okna dialogowego.

Użyj `CTreeView`, jeśli chcesz, aby kontrolka drzewa działała jak okno widoku w architekturze dokumentu/widoku, a także jako formant drzewa. `CTreeView` zajmie cały obszar klienta okna ramki lub okna rozdzielacza. Zostanie automatycznie zmieniony rozmiar po zmianie rozmiaru okna nadrzędnego i może przetwarzać komunikaty poleceń z menu, klawiszy skrótów i pasków narzędzi. Ponieważ kontrolka drzewa zawiera dane niezbędne do wyświetlenia drzewa, odpowiedni obiekt dokumentu nie musi być skomplikowany — można nawet użyć [CDocument](../mfc/reference/cdocument-class.md) jako typu dokumentu w szablonie dokumentu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
