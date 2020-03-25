---
title: Błąd PRJ0016 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 0cab1e35a36ab78426923d60acafb5cdf2942469
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192747"
---
# <a name="project-build-error-prj0016"></a>Błąd PRJ0016 kompilacji projektu

Ustawienia zabezpieczeń użytkownika uniemożliwiają utworzenie procesu. Te ustawienia są wymagane do kompilowania.

Użytkownik jest zalogowany jako użytkownik, który nie ma uprawnień do tworzenia procesów przy użyciu procesu. Należy zmienić poziomy uprawnień dla tego konta użytkownika lub skontaktować się z administratorem konta.

Ten błąd może również wystąpić, jeśli ustawiono następujący klucz rejestru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Aby rozwiązać ten problem, Usuń klucz RestrictRun. Jeśli ten klucz rejestru jest wymagany, Dołącz **VCSpawn. exe** do listy wpisów w kluczu.

Inną przyczyną tego błędu jest to, że ustawienie zasad nie obejmuje VCSpawn. exe w kluczu rejestru, HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako dozwolony program okna dla tego konta użytkownika.

Aby uzyskać dodatkowe informacje, zobacz temat [zgodne z ustawieniami zasad systemu](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings), w sekcji "uruchamianie tylko dozwolonych aplikacji systemu Windows".
