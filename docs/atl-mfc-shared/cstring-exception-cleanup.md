---
title: CString — oczyszczanie wyjątków
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: 48c8f1c0040236a4f7bf27a2d5ad985ae343c03a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222059"
---
# <a name="cstring-exception-cleanup"></a>CString — oczyszczanie wyjątków

W poprzednich wersjach MFC ważne było czyszczenie [CString](../atl-mfc-shared/reference/cstringt-class.md) obiektów po użyciu. W przypadku biblioteki MFC w wersji 3,0 lub nowszej czyszczenie jawne nie jest już konieczne.

W ramach mechanizmu obsługi wyjątków C++, który jest obecnie stosowany przez MFC, nie trzeba martwić się o czyszczenie po wystąpieniu wyjątku. Aby uzyskać opis sposobu, w jaki C++ "rozwinięcia" stosu po przechwyceniu wyjątku, zobacz [Instrukcje try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md). Nawet jeśli korzystasz ze środowiska MFC **try** / **catch** zamiast słów kluczowych języka c++ **`try`** i **`catch`** , MFC używa mechanizmu wyjątków c++ poniżej, więc nie trzeba czyścić jawnie.

## <a name="see-also"></a>Zobacz także

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
