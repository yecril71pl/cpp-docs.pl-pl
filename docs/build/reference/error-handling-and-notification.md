---
title: Obsługa błędów oraz powiadomienia
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 845a79e035943dbbde0d498702f70ec7dd6b4d3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432403"
---
# <a name="error-handling-and-notification"></a>Obsługa błędów oraz powiadomienia

Aby uzyskać więcej informacji na temat obsługi błędów oraz powiadomienia, zobacz [ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md).

Aby uzyskać więcej informacji na temat funkcji punktów zaczepienia, zobacz [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md).

Jeśli program używa bibliotek DLL załadowanych z opóźnieniem, jego musi obsługiwać błędy niezawodnie ponieważ nieobsłużone wyjątki będą powodować błędy, które występują, gdy program jest uruchomiony. Obsługa błędów składa się z dwóch części:

Odzyskiwanie danych za pomocą punktów zaczepienia.
Jeśli Twój kod musi odzyskać lub zapewnienia alternatywnej biblioteki i/lub procedura w przypadku niepowodzenia, zaczepienia można przekazać do funkcji pomocnika, która może podać lub rozwiązać ten problem. Nadal musi rutynowych hook wróć odpowiednią wartość przetwarzania (HINSTANCE lub FARPROC) lub 0, aby wskazać, że należy zgłosić wyjątek. Jego można również wyjątku własnej lub **longjmp** poza punkt zaczepienia. Istnieją punkty zaczepienia powiadomień i punkty zaczepienia błędów.

Raportowanie przy użyciu wyjątku.
Jeśli wszystko, co jest niezbędne do obsługi błędu jest przerwanie procedurą, hook nie jest tak długo, jak tylko kod użytkownika może obsłużyć wyjątek.

W poniższych tematach omówiono, obsługa błędów oraz powiadomienia:

- [Punkty zaczepienia powiadomień](../../build/reference/notification-hooks.md)

- [Punkty zaczepienia błędów](../../build/reference/failure-hooks.md)

- [Wyjątki](../../build/reference/exceptions-c-cpp.md)

## <a name="see-also"></a>Zobacz też

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)