---
title: "@ (Określ plik odpowiedzi kompilatora) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '@'
dev_langs: C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fcbadb55b2116b0939bbb954e4f544c40caacebb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="-specify-a-compiler-response-file"></a>@ (Określ plik odpowiedzi kompilatora)
Określa plik odpowiedzi kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Plik tekstowy zawierający polecenia kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Plik odpowiedzi może zawierać dowolne polecenia, które należy określić w wierszu polecenia. Może to być przydatne, jeśli jego argumenty wiersza polecenia przekracza 127 znaków.  
  
 Nie jest możliwe określenie  **@**  opcję w pliku odpowiedzi. Oznacza to, że plik odpowiedzi nie można osadzić inny plik odpowiedzi.  
  
 W wierszu polecenia można określić dowolną liczbę opcji pliku odpowiedzi (na przykład `@respfile.1 @respfile.2`) można dowolnie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
-   Plik odpowiedzi nie można określić z środowiska programistycznego i musi być określona w wierszu polecenia.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Nie można zmienić tej opcji kompilatora programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)