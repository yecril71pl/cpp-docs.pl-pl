---
title: "Pliki poleceń CL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a711b2f4a484a6370af828c5d0aad522686ca3f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cl-command-files"></a>Pliki poleceń CL
Plik polecenia to plik tekstowy, który zawiera opcje i nazwy plików, w przeciwnym razie należy wpisać w [wiersza polecenia](../../build/reference/compiler-command-line-syntax.md) lub określić za pomocą [zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md). CL akceptuje pliku poleceń kompilatora jako argumentu w zmiennej środowiskowej CL lub w wierszu polecenia. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.  
  
 Opcje i nazwy plików w pliku poleceń są przetwarzane zgodnie z lokalizacją polecenia nazwy pliku w zmiennej środowiskowej CL lub w wierszu polecenia. Jeśli opcja/Link pojawia się w pliku poleceń, wszystkie opcje na pozostałą część wiersza są przekazywane do konsolidatora. Opcje w kolejnych wierszy w pliku poleceń i opcji wiersza polecenia po wywołaniu pliku polecenia nadal są akceptowane jako opcje kompilatora. Aby uzyskać więcej informacji na wpływ ich interpretacji kolejność opcji, zobacz [kolejność opcji CL](../../build/reference/order-of-cl-options.md).  
  
 Plik poleceń nie może zawierać polecenia CL. Każda opcja muszą się rozpoczynać i kończyć się w tym samym wierszu; Nie można użyć kreska ułamkowa odwrócona (\\) do łączenia z opcją między dwoma liniami.  
  
 Pliku poleceń jest określona przez znak @ (@) następuje filename; Nazwa pliku można określić ścieżkę bezwzględną ani względną.  
  
 Jeśli na przykład następujące polecenie znajduje się w pliku o nazwie Odp.:  
  
```  
/Og /link LIBC.LIB  
```  
  
 i określ polecenie CL:  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 polecenie CL wygląda następująco:  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 Należy pamiętać, efektywnie łączyć wiersza polecenia i polecenia pliku polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)