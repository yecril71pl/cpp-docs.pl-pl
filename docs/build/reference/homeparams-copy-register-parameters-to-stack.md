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
ms.openlocfilehash: bfd6b8c77d972eb4606e7095bc5f733e7db16ea6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464979"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopiuj parametry rejestru do stosu)
Wymusza zapisanie parametrów przekazanych w rejestrach były zapisywane do ich lokalizacji na stosie wejściu do funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja kompilatora jest tylko w przypadku x64 kompilatory (kompilacja natywna i krzyżowa).  
  
 Gdy parametry są przekazywane w x64 kompilacji, Konwencje wywoływania wymagają stackspace dla parametrów, nawet w przypadku parametrów przekazanych w rejestrach. Aby uzyskać więcej informacji, zobacz [przekazywania parametru](../../build/parameter-passing.md). Jednak domyślnie kompilację wydania Parametry rejestru nie zostaną zapisane na stosie, do obszaru, który znajduje się już dla parametrów. Utrudnia to debugowanie zoptymalizowanego (wersja) kompilacji programu.  
  
 W przypadku kompilacji wydania, użyj **/homeparams** aby upewnić się, że można debugować aplikację. **/ homeparams** pociąga uprzywilejowanych wydajność, ponieważ jest wymagane cyklu załadować Parametry rejestru do stosu.  
  
 Do kompilacji debugowanej stos zawsze jest wypełniana parametry przekazywane w rejestrach.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** stronę właściwości.  
  
4.  Wpisz opcje kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)