---
title: Określanie nazwy ścieżki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2dd121909fbe0aa2f9305b7bd5779b995a69719
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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