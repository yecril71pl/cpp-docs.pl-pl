---
title: "Obsługa standardu Unicode w kompilatorze i Konsolidatorze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs: C++
helpviewer_keywords: Unicode, Visual C++
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15fefc4cc44edfd67bd8ba89ab68c6965c8639a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze
W tym temacie opisano obsługi formatu Unicode w narzędziach Visual C++ w kompilacji.  
  
 Nazwy plików  
 Określona w wierszu polecenia lub w dyrektywy kompilatora nazw plików (takich jak #include) teraz może zawierać znaków Unicode.  
  
 Pliki kodu źródłowego  
 Znaki Unicode są teraz obsługiwane w identyfikatory, makra, literały ciągów i znakowe i komentarze.  Uniwersalne nazwy znaków teraz również są obsługiwane.  
  
 Unicode można wprowadzić do pliku kodu źródłowego w następujących kodowań:  
  
-   UTF-16 little endian z lub bez znacznika kolejności bajtów (BOM)  
  
-   UTF-16 big endian z lub bez BOM  
  
-   UTF-8 z BOM  
  
 Dane wyjściowe  
 Podczas kompilacji kompilator generuje diagnostyczne w konsoli, UTF-16.  Znaki, które mogą być wyświetlane w konsoli są zależne od właściwości okna konsoli.  Dane wyjściowe kompilatora, przekierowywany do pliku jest bieżąca strona kodowa konsoli ANSI.  
  
 Pliki odpowiedzi konsolidatora i. Pliki DEF  
 Pliki odpowiedzi i DEF, pliki mogą być albo UTF-16 znacznika kolejności bajtów lub ANSI.  Wcześniej była obsługiwana tylko ANSI.  
  
 zrzuty .asm i .cod  
 zrzuty .asm i .cod są w formacie ANSI domyślnie w celu zapewnienia zgodności z MASM.  Umożliwia /FAu output UTF-8.  Zauważ, że jeśli określisz/FAS, intermingled źródła tylko bezpośrednio wydruku i może wyglądać zniekształcony, na przykład jeśli kod źródłowy jest UTF-8 i nie określono /FAsu.  
  
 Można włączyć nazwy plików Unicode w środowisku programistycznym (zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)), wybierając odpowiednie narzędzia i wybierając **włączyć plików odpowiedzi Unicode** właściwość które jest domyślnie włączone. Jedną z przyczyn może zmienić to ustawienie domyślne to można zmodyfikować środowiska deweloperskiego do używania kompilatora, który nie ma obsługi formatu Unicode.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowania kodu C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md)