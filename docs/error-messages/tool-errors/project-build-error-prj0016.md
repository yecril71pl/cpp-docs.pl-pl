---
title: Błąd PRJ0016 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: ada89b074fd8e0c2bfc75ba833e9c5966a145312
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616869"
---
# <a name="project-build-error-prj0016"></a>Błąd PRJ0016 kompilacji projektu

Ustawienia zabezpieczeń użytkownika uniemożliwić tworzony przez proces. Te ustawienia są wymagane do kompilowania.

Zalogowano Cię jako użytkownik, który nie ma uprawnień do tworzenia procesów za pomocą procesu. Zmień poziomy uprawnień dla tego konta użytkownika lub skontaktuj się z administratorem konta.

Ten błąd może również wystąpić, jeśli ustawiono następujący klucz rejestru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Aby rozwiązać ten problem, Usuń klucz RestrictRun. Jeśli ten klucz rejestru jest potrzebny, należy dołączyć **vcspawn.exe** listę wpisów w kluczu.

Inną przyczyną tego błędu jest to, że ustawienia zasad nie obejmuje VCSpawn.exe w kluczu rejestru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako program okna dozwolone dla tego konta użytkownika.

Aby uzyskać więcej informacji, zobacz [przestrzega ustawienia zasad systemu](https://msdn.microsoft.com/library/aa372139), w sekcji "Uruchom tylko dozwolone aplikacje Windows".