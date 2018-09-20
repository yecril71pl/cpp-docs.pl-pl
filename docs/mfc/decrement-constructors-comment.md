---
title: — Komentarz / / constructors | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f03a65c3f870b1e7648f03b70efe7242c35a21f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429360"
---
# <a name="-constructors-comment"></a>Komentarz // Constructors

`// Constructors` Część deklaracji klasy MFC deklaruje konstruktorów (w sensie C++), a także wszystkie funkcje inicjowania musieli naprawdę używa obiektu. Na przykład `CWnd::Create` znajduje się w sekcji konstruktorów, ponieważ przed użyciem `CWnd` obiektu musi być "pełni skonstruowany" przez pierwsze wywołanie konstruktora, C++, a następnie wywołując `Create` funkcji. Zazwyczaj te elementy członkowskie są publiczne.

Na przykład klasy `CStdioFile` ma trzy konstruktory, z których jeden jest wyświetlany na liście w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Komentarz / / Implementation](../mfc/decrement-implementation-comment.md)<br/>
[Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Komentarz / / Operations](../mfc/decrement-operations-comment.md)<br/>
[Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

