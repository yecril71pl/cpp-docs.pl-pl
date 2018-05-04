---
title: -homeparams (Kopiuj Parametry rejestru do stosu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffc9b37ebdcbb380186c7840f5ebd956708a2dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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