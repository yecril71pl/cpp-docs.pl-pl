---
title: Cstring — Oczyszczanie wyjątku
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: f1950553e3bf3a43f029478e00b177f5cbfe121f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492550"
---
# <a name="cstring-exception-cleanup"></a>Cstring — Oczyszczanie wyjątku

W poprzednich wersjach biblioteki MFC, konieczne jest czyszczenie [CString](../atl-mfc-shared/reference/cstringt-class.md) obiektów po użyciu. Za pomocą MFC w wersji 3.0 i nowszych jawnego usuwania z pamięci nie jest już konieczne.

W obszarze mechanizm, który używa teraz MFC obsługi wyjątków C++ nie masz już martwić się o czyszczenia po wystąpieniu wyjątku. Aby uzyskać opis sposobu C++ "rozwija" stos po Wystąpił wyjątek, zobacz [try, catch i throw — instrukcje](../cpp/try-throw-and-catch-statements-cpp.md). Nawet w przypadku używania MFC **SPRÓBUJ**/**CATCH** makr zamiast słowa kluczowe języka C++ **spróbuj** i **catch**, MFC wykorzystuje języka C++ mechanizm wyjątków poniżej, dzięki czemu możesz nadal nie trzeba jawnie wyczyścić.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

