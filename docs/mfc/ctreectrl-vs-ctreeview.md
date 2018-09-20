---
title: CTreeCtrl a CTreeView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs:
- C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8acaecbdfb99b8ae0b27023145a0ef6aee1f219
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399154"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl a CTreeView

Biblioteka MFC zawiera dwie klasy, które hermetyzują kontrolkach drzewa: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) i [CTreeView](../mfc/reference/ctreeview-class.md). Każda klasa przydaje się w różnych sytuacjach.

Użyj `CTreeCtrl` gdy będziesz potrzebować kontrolki okna zwykły podrzędnej; na przykład w oknie dialogowym. Szczególnie chcesz użyć `CTreeCtrl` Jeśli nastąpi innych formantów podrzędnych w oknie, tak jak w typowej okno dialogowe.

Użyj `CTreeView` kiedy zechcesz, formant drzewa, aby zachowywać się jak okno Widok, w ramach architektury dokument/widok, a także formantu drzewa. A `CTreeView` zajmie całego obszaru klienta ramki okna lub okna rozdzielacza. Jego rozmiar będzie automatycznie zmieniany po zmianie rozmiaru okna nadrzędnego, a może przetworzyć polecenia wiadomości z menu, klawisze skrótów i paski narzędzi. Ponieważ formantu drzewa zawiera dane niezbędne do wyświetlania w drzewie, odpowiedni obiekt dokumentu nie ma być skomplikowane — można nawet używać [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu w szablonie dokumentu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

