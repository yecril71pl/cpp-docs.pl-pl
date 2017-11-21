---
title: "Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- include
- Lib
- Path
dev_langs: C++
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: babca0fb75748f95d36a7afdd3c76be4419abc43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia

Narzędzia wiersza polecenia kompilacji Visual C++ wymaga kilku zmiennych środowiskowych, które są dostosowane do instalacji i kompilacji konfiguracji. Po zainstalowaniu przez obciążenie C++ [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Instalatora, tworzy polecenia niestandardowych plików lub pliki wsadowe, które Ustaw zmienne środowiskowe wymagane. Instalator używa następnie te pliki poleceń do tworzenia skrótów do menu Start systemu Windows otworzyć okno wiersza polecenia dewelopera. Te skróty Ustawianie zmiennych środowiskowych dla określonego Konfiguracja kompilacji. Jeśli chcesz użyć narzędzia wiersza polecenia, można wykonać jedną z tych skrótów lub można Otwórz okno wiersza polecenia zwykły, a następnie uruchom jeden z plików polecenia niestandardowych samodzielnie ustawić środowisko konfiguracyjne kompilacji. Aby uzyskać więcej informacji, zobacz [kompilacji kodu C/C++ w wierszu polecenia](building-on-the-command-line.md).  
  
Narzędzia wiersza polecenia programu Visual C++ używać zmiennych środowiskowych PATH, TMP INCLUDE, LIB i LIBPATH, a także używać inne specyficzne dla programu zainstalowanych narzędzi, platform i zestawy SDK zmiennych środowiskowych. Nawet prosty [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalacji mogą ustawiać 20 lub więcej zmiennych środowiskowych. Ponieważ wartości te zmienne środowiskowe są specyficzne dla instalacji i wybraną konfigurację kompilacji i może zostać zmieniona przez uaktualnienia i aktualizacje produktu, zaleca się użycie skrótów wiersza polecenia dewelopera lub jednego z pliki poleceń dostosowane ustawienia, zamiast ich ustawienie w środowisku Windows samodzielnie. 

Aby zobaczyć, które zmienne środowiskowe są ustawiane przez skrót do wiersza polecenia dewelopera, można użyć polecenia SET. Otwórz okno wiersza polecenia zwykłe i Przechwyć dane wyjściowe polecenia SET dla linii bazowej. Otwórz okno wiersza polecenia dewelopera i Przechwyć dane wyjściowe polecenia SET do porównania. Narzędzia obsługującego różnice, takie jak wbudowana w środowisku IDE programu Visual Studio może być przydatne do porównywania zmienne środowiskowe i zobacz, co jest ustawiana przez deweloperów. Informacje o zmiennych w danym środowisku używany przez kompilator i konsolidatora, zobacz [zmienne środowiskowe](../build/reference/cl-environment-variables.md) i [zmienne środowiskowe LINK](../build/reference/link-environment-variables.md).  
  
> [!NOTE]
>  Kilku narzędzi wiersza polecenia lub opcje narzędzia mogą wymagać uprawnienia administratora. Jeśli masz problemy z uprawnieniami, korzystając z nich, zaleca się Otwórz okno wiersza polecenia dewelopera przy użyciu **Uruchom jako Administrator** opcji. W systemie Windows 10, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów okna wiersza polecenia, a następnie wybierz **więcej**, **Uruchom jako administrator**.  
  
## <a name="see-also"></a>Zobacz też  

[Kompilowania kodu C/C++ w wierszu polecenia](../build/building-on-the-command-line.md)   
[Łączenie](../build/reference/linking.md)   
[Opcje konsolidatora](../build/reference/linker-options.md)   
[Kompilowanie programu C/C++](../build/reference/compiling-a-c-cpp-program.md)   
[Opcje kompilatora](../build/reference/compiler-options.md)