---
title: --Komentarz / / Overridables
ms.date: 11/04/2016
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
ms.openlocfilehash: 90d6a585f62de589299147edce87332d96c6dbb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153241"
---
# <a name="-overridables-comment"></a>Komentarz // Overridables

`// Overridables` Część deklaracji klasy MFC zawiera funkcje wirtualne, które można przesłonić w klasie pochodnej, gdy trzeba zmienić zachowanie klasy bazowej. Są zwykle nazywane począwszy od "Włączone" mimo że nie jest bezwzględnie konieczne. Tutaj są przeznaczone do można przesłonić i często implementuje lub udostępnienia pewnego rodzaju "wywołanie zwrotne" lub "dołączyć". Zazwyczaj te elementy członkowskie są chronione.

W MFC sam czystych funkcji wirtualnych są zawsze umieszczane w tej sekcji. Czystej funkcji wirtualnej w języku C++ jest jednym z formularza:

`virtual void OnDraw( ) = 0;`

W przykładzie z klasy `CStdioFile`w [przykład komentarzy](../mfc/an-example-of-the-comments.md), lista zawiera żadna sekcja / / overridables. Klasa `CDocument`, z drugiej strony, Wyświetla około 10 możliwym do zastąpienia elementów członkowskich.

W niektórych klas, może również zostać wyświetlony komentarz `// Advanced Overridables`. Są to funkcje, które tylko zaawansowanych programistów powinien próbować zastąpić. Najprawdopodobniej nigdy nie należy je zastąpić.

> [!NOTE]
>  Konwencje opisanych w tym artykule również działać poprawnie, ogólnie rzecz biorąc, właściwości i metod automatyzacji (wcześniej znane jako automatyzacji OLE). Metody automatyzacji są podobne do operacji MFC. Właściwości automatyzacji są podobne do atrybutów MFC. Właściwości zdarzeń automatyzacji (obsługiwane dla kontrolek ActiveX, znana wcześniej jako formantów OLE) są podobne do elementów członkowskich MFC możliwym do zastąpienia.

## <a name="see-also"></a>Zobacz także

[Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Przykład komentarzy](../mfc/an-example-of-the-comments.md)<br/>
[Komentarz / / Implementation](../mfc/decrement-implementation-comment.md)<br/>
[Komentarz / / constructors](../mfc/decrement-constructors-comment.md)<br/>
[Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Komentarz / / Operations](../mfc/decrement-operations-comment.md)
