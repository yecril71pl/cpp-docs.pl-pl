---
title: Błąd PRJ0016 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c07de9e766b7c2126d0ce4c8d1daed631a8355c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194743"
---
# <a name="project-build-error-prj0016"></a>Błąd PRJ0016 kompilacji projektu
Ustawienia zabezpieczeń użytkownika uniemożliwić tworzony przez proces. Te ustawienia są wymagane do kompilowania.  
  
 Zalogowano Cię jako użytkownik, który nie ma uprawnień do tworzenia procesów za pomocą procesu. Zmień poziomy uprawnień dla tego konta użytkownika lub skontaktuj się z administratorem konta.  
  
 Ten błąd może również wystąpić, jeśli ustawiono następujący klucz rejestru:  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 Aby rozwiązać ten problem, Usuń klucz RestrictRun. Jeśli ten klucz rejestru jest potrzebny, należy dołączyć **vcspawn.exe** listę wpisów w kluczu.  
  
 Inną przyczyną tego błędu jest to, że ustawienia zasad nie obejmuje VCSpawn.exe w kluczu rejestru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako program okna dozwolone dla tego konta użytkownika.  
  
 Aby uzyskać dodatkowe informacje Zobacz:  
  
-   Artykuł bazy wiedzy 324153, która jest dostępna na [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).  
  
-   [Dostosowanie się do ustawienia zasad systemu](https://msdn.microsoft.com/library/aa372139), sekcję "Uruchom tylko dozwolone aplikacje Windows".