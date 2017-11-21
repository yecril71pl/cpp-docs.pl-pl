---
title: "Błąd PRJ0016 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0016
dev_langs: C++
helpviewer_keywords: PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aa96ec353dbe236744a6a9baa5ad18ff25451d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0016"></a>Błąd PRJ0016 kompilacji projektu
Ustawienia zabezpieczeń użytkownika uniemożliwić tworzony przez proces. Te ustawienia są wymagane do kompilacji.  
  
 Użytkownik jest zalogowany jako użytkownik, który nie ma uprawnień do tworzenia procesów przy użyciu procesu. Zmienianie poziomów uprawnień dla tego konta użytkownika lub skontaktuj się z administratorem konta.  
  
 Ten błąd może również wystąpić, jeśli ustawiono następujący klucz rejestru:  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 Aby rozwiązać ten problem, Usuń klucz RestrictRun. Jeśli ten klucz rejestru nie jest konieczne, dołącz **vcspawn.exe** do listy wpisów w kluczu.  
  
 Inną przyczyną tego błędu jest to, że ustawienia zasad nie obejmuje VCSpawn.exe w kluczu rejestru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako dozwolone program okna dla tego konta użytkownika.  
  
 Aby uzyskać dodatkowe informacje Zobacz:  
  
-   Artykuł bazy wiedzy 324153, który jest dostępny na [http://support.microsoft.com/default.aspx?scid=kb;en-us;324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).  
  
-   [Do ustawienia zasad systemu](http://msdn.microsoft.com/library/aa372139), sekcję "Uruchamiaj tylko dozwolone aplikacje systemu Windows".