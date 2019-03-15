---
title: Obsługa błędów oraz powiadomienia
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 29fe46e15712609ec0c4f268749aaefed103117e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812944"
---
# <a name="error-handling-and-notification"></a>Obsługa błędów oraz powiadomienia

Aby uzyskać więcej informacji na temat obsługi błędów oraz powiadomienia, zobacz [ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md).

Aby uzyskać więcej informacji na temat funkcji punktów zaczepienia, zobacz [struktura i stała — definicje](structure-and-constant-definitions.md).

Jeśli program używa bibliotek DLL załadowanych z opóźnieniem, jego musi obsługiwać błędy niezawodnie ponieważ nieobsłużone wyjątki będą powodować błędy, które występują, gdy program jest uruchomiony. Obsługa błędów składa się z dwóch części:

Odzyskiwanie danych za pomocą punktów zaczepienia.
Jeśli Twój kod musi odzyskać lub zapewnienia alternatywnej biblioteki i/lub procedura w przypadku niepowodzenia, zaczepienia można przekazać do funkcji pomocnika, która może podać lub rozwiązać ten problem. Nadal musi rutynowych hook wróć odpowiednią wartość przetwarzania (HINSTANCE lub FARPROC) lub 0, aby wskazać, że należy zgłosić wyjątek. Jego można również wyjątku własnej lub **longjmp** poza punkt zaczepienia. Istnieją punkty zaczepienia powiadomień i punkty zaczepienia błędów.

Raportowanie przy użyciu wyjątku.
Jeśli wszystko, co jest niezbędne do obsługi błędu jest przerwanie procedurą, hook nie jest tak długo, jak tylko kod użytkownika może obsłużyć wyjątek.

W poniższych tematach omówiono, obsługa błędów oraz powiadomienia:

- [Punkty zaczepienia powiadomień](notification-hooks.md)

- [Punkty zaczepienia błędów](failure-hooks.md)

- [Wyjątki](exceptions-c-cpp.md)

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
