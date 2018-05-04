---
title: Argumenty dla metody main | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 544b5eaba49fff0a5f2b3111c2a5f7fe42c9b2ee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="arguments-to-main"></a>Argumenty dla metody main
**ANSI 2.1.2.2.1** semantykę argumenty dla metody main  
  
 W programie Microsoft C jest wywoływana funkcja wywoływana w momencie uruchamiania programu **głównego**. Nie istnieje bez prototypu zadeklarowanym dla **głównego**, a mogą być definiowane z zero, dwie lub trzy parametry:  
  
```  
int main( void )  
int main( int argc, char *argv[] )  
int main( int argc, char *argv[], char *envp[] )  
```  
  
 Trzeci wiersz powyżej, gdzie **głównego** akceptuje trzy parametry, to rozszerzenie Microsoft ze standardem ANSI C. Trzeci parametr **envp —**, jest tablicy wskaźników do zmiennych środowiskowych. **Envp —** tablicy jest został przerwany przez wskaźnika o wartości null. Zobacz [funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md) uzyskać więcej informacji o **głównego** i **envp —**.  
  
 Zmienna **argc —** nigdy nie przechowuje wartości ujemnej.  
  
 Tablica ciągów kończy się wyrazem **ARGV — [argc —]**, który zawiera wskaźnika o wartości null.  
  
 Wszystkie elementy **ARGV —** tablicy są wskaźnikami do ciągów.  
  
 Program wywołać bez argumentów wiersza polecenia otrzyma wartość jednego dla **argc —**, ponieważ nazwa pliku wykonywalnego jest umieszczana w **ARGV — [0]**. (W wersjach systemu MS-DOS przed 3.0, nazwa pliku wykonywalnego nie jest dostępna. Litera "C" znajduje się w **ARGV — [0]**.) Ciągi wskazywana przez **ARGV — [1]** za pośrednictwem **ARGV — [argc — - 1]** reprezentują parametry.  
  
 Parametry **argc —** i **ARGV —** można modyfikować i zachowywanie ich wartości przechowywane ostatnich między programów, uruchamianie i kończenie działania programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Środowisko](../c-language/environment.md)