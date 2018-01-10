---
title: Korzystanie z VERIFY zamiast ASSERT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: assert
dev_langs: C++
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ffe046a281bbbbefc251b48df55ecd275515e60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-verify-instead-of-assert"></a>Korzystanie z VERIFY zamiast ASSERT
Załóżmy, że po uruchomieniu wersji do debugowania aplikacji MFC nie ma żadnych problemów. Jednak wydanej wersji programu ta sama aplikacja ulegnie awarii, zwraca niepoprawne wyniki i/lub wykazuje nietypowe zachowanie.  
  
 Ten problem może być spowodowany umieść kod ważne w instrukcji ASSERT, aby sprawdzić, czy wykonuje poprawnie. Ponieważ ASSERT-instrukcje są oznaczone jako komentarz w kompilacji wydania programu MFC, kod nie działa w kompilacji wydania.  
  
 Jeśli używasz ASSERT, aby upewnić się, że wywołanie funkcji zakończyła się pomyślnie, należy rozważyć użycie [Sprawdź](../../mfc/reference/diagnostic-services.md#verify) zamiast tego. VERIFY-makro ocenia argumenty w obu debug i release kompiluje aplikacji.  
  
 Inny preferowanego technika jest przypisanie do zmiennej tymczasowej wartości zwracanej przez funkcję, a następnie przetestować zmiennej w instrukcji potwierdzenia.  
  
 Sprawdź poniższy fragment kodu:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 Ten kod zadziała doskonale wersję do debugowania aplikacji MFC. Jeśli wywołanie `calloc( )` kończy się niepowodzeniem, diagnostycznych wiadomość zawierającą liczbę plików i wierszy jest wyświetlana. Jednak w sprzedaży detalicznej kompilację aplikacji MFC:  
  
-   wywołanie `calloc( )` nigdy nie wystąpi, pozostawiając `buf` niezainicjowana, lub  
  
-   `strcpy_s( )`kopie "`Hello, World`" do losowe część pamięci, prawdopodobnie awarii aplikacji lub powoduje system przestanie odpowiadać, lub  
  
-   `free()`próbuje zwolnić pamięć, które nigdy nie zostało przydzielone.  
  
 Aby użyć ASSERT poprawnie, należy zmienić przykładowy kod do następującego:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );  
ASSERT( buf != NULL );  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 Lub sprawdź, czy można użyć zamiast tego:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)