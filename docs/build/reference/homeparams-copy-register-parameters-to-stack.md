---
title: -homeparams (Kopiuj Parametry rejestru do stosu) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /homeparams
dev_langs: C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fff1b206620ef9efee3fc22c83c8d5317e99b607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopiuj parametry rejestru do stosu)
Wymusza parametry przekazywane w rejestrach były zapisywane miejsca na stosie wejścia funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja kompilatora jest tylko w przypadku [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilatory (natywne i Międzyplatformowe kompilacji).  
  
 Jeśli parametry są przekazywane w [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilacji, konwencji wywoływania wymagają stackspace dla parametrów, nawet w przypadku parametry przekazywane w rejestrach. Aby uzyskać więcej informacji, zobacz [przekazywanie parametru](../../build/parameter-passing.md). Jednak domyślnie w kompilacji wydania Parametry rejestru nie zostaną zapisane na stos do obszaru jest już podany dla parametrów. Utrudnia debugowanie zoptymalizowanego (wersja) kompilacji programu.  
  
 Dla kompilacji wydania, należy użyć **/homeparams** aby upewnić się, że można debugować aplikacji. **/ homeparams** oznacza uprzywilejowanych wydajności, ponieważ wymagają cyklu załadować Parametry rejestru do stosu.  
  
 W kompilację debugowania stosu zawsze jest wypełniana parametry przekazywane w rejestrach.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)