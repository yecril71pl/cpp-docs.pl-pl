---
title: Błąd PRJ0016 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 6733ef1f390f2ff377356dda3f7cd3ebfe10cc2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509886"
---
# <a name="project-build-error-prj0016"></a>Błąd PRJ0016 kompilacji projektu

Ustawienia zabezpieczeń użytkownika uniemożliwiają utworzenie procesu. Te ustawienia są wymagane do kompilowania.

Użytkownik jest zalogowany jako użytkownik, który nie ma uprawnień do tworzenia procesów przy użyciu procesu. Należy zmienić poziomy uprawnień dla tego konta użytkownika lub skontaktować się z administratorem konta.

Ten błąd może również wystąpić, jeśli ustawiono następujący klucz rejestru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Aby rozwiązać ten problem, Usuń klucz RestrictRun. Jeśli ten klucz rejestru jest wymagany, Dołącz **VCSpawn. exe** do listy wpisów w kluczu.

Inną przyczyną tego błędu jest to, że ustawienie zasad nie zawiera VCSpawn. exe w kluczu rejestru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako dozwolony program okna dla tego konta użytkownika.

Aby uzyskać dodatkowe informacje, zobacz temat [zgodne z ustawieniami zasad systemu](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings), w sekcji "uruchamianie tylko dozwolonych aplikacji systemu Windows".