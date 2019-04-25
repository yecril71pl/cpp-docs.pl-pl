---
title: — Komentarz dotyczący konstruktorów
ms.date: 11/04/2016
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
ms.openlocfilehash: e0d02af016a0c7bfb0869b7cdd30fe0db2975102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240864"
---
# <a name="-constructors-comment"></a>Komentarz // Constructors

`// Constructors` Część deklaracji klasy MFC deklaruje konstruktorów (w sensie C++), a także wszystkie funkcje inicjowania musieli naprawdę używa obiektu. Na przykład `CWnd::Create` znajduje się w sekcji konstruktorów, ponieważ przed użyciem `CWnd` obiektu musi być "pełni skonstruowany" przez pierwsze wywołanie konstruktora, C++, a następnie wywołując `Create` funkcji. Zazwyczaj te elementy członkowskie są publiczne.

Na przykład klasy `CStdioFile` ma trzy konstruktory, z których jeden jest wyświetlany na liście w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Zobacz także

[Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Komentarz / / Implementation](../mfc/decrement-implementation-comment.md)<br/>
[Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Komentarz / / Operations](../mfc/decrement-operations-comment.md)<br/>
[Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)
