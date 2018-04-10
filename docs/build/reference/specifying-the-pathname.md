---
title: Określanie nazwy ścieżki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2412ab15317604e1d6cccc5535226d429d8ba6b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-pathname"></a>Określanie nazwy ścieżki
Każda opcja pliku wyjściowego akceptuje *pathname* argumentu, który można określić lokalizację i nazwę pliku wyjściowego. Argument może zawierać nazwy dysku, katalogu i nazwa pliku. Nie może być spacji między opcją i argument.  
  
 Jeśli *pathname* zawiera nazwę pliku bez rozszerzenia, kompilator zapewnia dane wyjściowe domyślne rozszerzenie. Jeśli *pathname* obejmuje katalogu, ale brak nazwy pliku kompilatora tworzy plik o nazwie domyślnej w określonym katalogu. Domyślna nazwa opiera się na podstawową nazwę pliku źródłowego i domyślne rozszerzenie na podstawie typu pliku wyjściowego. Jeśli opuścisz *pathname* całkowicie, kompilator tworzy plik o nazwie domyślnej w domyślnym folderze.  
  
 Alternatywnie *pathname* argument może być nazwa urządzenia (AUX, CON, PRN lub NUL), a nie nazwę pliku. Nie należy używać odstęp między opcji i nazwę urządzenia lub dwukropka jako część nazwy urządzenia.  
  
|Nazwa urządzenia|Reprezentuje|  
|-----------------|----------------|  
|AUX|Urządzenie pomocnicze|  
|KON|Konsola|  
|PRN|Drukarki|  
|NUL|Urządzenie NULL (nie utworzony plik)|  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu wysyła pliku mapowania do drukarki:  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)