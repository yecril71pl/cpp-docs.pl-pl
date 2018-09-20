---
title: Cstring — Oczyszczanie wyjątku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81349135fa822627cb40bdcd2570276d8040e50e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385524"
---
# <a name="cstring-exception-cleanup"></a>Cstring — Oczyszczanie wyjątku

W poprzednich wersjach biblioteki MFC, konieczne jest czyszczenie [CString](../atl-mfc-shared/reference/cstringt-class.md) obiektów po użyciu. Za pomocą MFC w wersji 3.0 i nowszych jawnego usuwania z pamięci nie jest już konieczne.

W obszarze mechanizm, który używa teraz MFC obsługi wyjątków C++ nie masz już martwić się o czyszczenia po wystąpieniu wyjątku. Aby uzyskać opis sposobu C++ "rozwija" stos po Wystąpił wyjątek, zobacz [try, catch i throw — instrukcje](../cpp/try-throw-and-catch-statements-cpp.md). Nawet w przypadku używania MFC **SPRÓBUJ**/**CATCH** makr zamiast słowa kluczowe języka C++ **spróbuj** i **catch**, MFC wykorzystuje języka C++ mechanizm wyjątków poniżej, dzięki czemu możesz nadal nie trzeba jawnie wyczyścić.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

