---
title: Flagi kontrolne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.flags
dev_langs: C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8c6f58e345669cb1898bc2717a7e42ddc8e2539
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="control-flags"></a>Flagi kontrolne
Wersja do debugowania biblioteki wykonawcze języka Microsoft C używa następujących flag kontroli alokacji sterty i proces raportowania. Aby uzyskać więcej informacji, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
|Flaga|Opis|  
|----------|-----------------|  
|[_CRTDBG_MAP_ALLOC —](../c-runtime-library/crtdbg-map-alloc.md)|Funkcje sterty podstawowej, aby ich odpowiedniki wersji debugowania mapy|  
|[_DEBUG](../c-runtime-library/debug.md)|Umożliwia korzystanie z debugowania wersje funkcji środowiska wykonawczego|  
|[_crtdbgflag —](../c-runtime-library/crtdbgflag.md)|Określa, jak Menedżer sterty debugowania śledzi alokacji|  
  
 Te flagi można zdefiniować za pomocą opcji wiersza polecenia /D lub z `#define` dyrektywy. Jeśli flaga jest zdefiniowana z `#define`, dyrektywa musi występować przed instrukcji dla deklaracji procedury obejmują plik nagłówka.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne i typy standardowe](../c-runtime-library/global-variables-and-standard-types.md)