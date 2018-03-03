---
title: Flagi kontrolne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71e0b1d01e291a1fa48740ccb6389a1b064433b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="control-flags"></a>Flagi kontrolne
Wersja do debugowania biblioteki wykonawcze języka Microsoft C używa następujących flag kontroli alokacji sterty i proces raportowania. Aby uzyskać więcej informacji, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
|Flaga|Opis|  
|----------|-----------------|  
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Funkcje sterty podstawowej, aby ich odpowiedniki wersji debugowania mapy|  
|[_DEBUG](../c-runtime-library/debug.md)|Umożliwia korzystanie z debugowania wersje funkcji środowiska wykonawczego|  
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Określa, jak Menedżer sterty debugowania śledzi alokacji|  
  
 Te flagi można zdefiniować za pomocą opcji wiersza polecenia /D lub z `#define` dyrektywy. Jeśli flaga jest zdefiniowana z `#define`, dyrektywa musi występować przed instrukcji dla deklaracji procedury obejmują plik nagłówka.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne i typy standardowe](../c-runtime-library/global-variables-and-standard-types.md)