---
title: W tym udostępnionych (tylko do odczytu) lub obliczonych symbole | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.shared.calculated
dev_langs:
- C++
helpviewer_keywords:
- symbols, read-only
- symbols, shared
- symbols, calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c56e8af65d27bda8ef04655f40bdd2e335067d3c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Włączanie symboli udostępnionych (tylko do odczytu) lub obliczonych
Środowisko projektowe odczytuje plik zasobów utworzony przez inną aplikację po raz pierwszy oznacza wszystkie pliki nagłówkowe dołączone jako tylko do odczytu. Następnie można użyć [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md) Aby dodać pliki nagłówkowe dodatkowego symbolu tylko do odczytu.  
  
 Jedną z przyczyn się, że chcesz używać definicje symbolu tylko do odczytu jest plików symboli, które firma zamierza udostępnić dla kilku projektów.  
  
 Jeśli masz istniejące zasoby z definicji symbolu, które umożliwia definiowanie wartości symbolu wyrażenia zamiast prostego liczb całkowitych, można także użyć plików dołączone symbolu. Na przykład:  
  
```  
#define   IDC_CONTROL1 2100  
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```  
  
 Środowisko będzie poprawnie zinterpretować te symbole obliczane tak długo, jak:  
  
-   Symbole obliczane są umieszczane w pliku symboli tylko do odczytu.  
  
-   Plik zasobów zawiera zasoby, do których te symbole obliczane są przydzielone.  
  
-   Oczekiwano wyrażenia liczbowego.  
  
> [!NOTE]
>  Jeśli Oczekiwano ciągu lub wyrażenia liczbowego wyrażenia nie jest oceniany.  
  
### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Aby uwzględnić symbole udostępnione (tylko do odczytu) w pliku zasobów  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc i wybierz [zasobów zawiera](../windows/resource-includes-dialog-box.md) z menu skrótów.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W **dyrektywy symboli tylko do odczytu** , używaj **#include** dyrektywy kompilatora, aby określić plik, w którym ma symbole tylko do odczytu, które mają być przechowywane.  
  
     Nie wywołuj pliku Resource.h, ponieważ jest nazwa pliku, zwykle używany przez plik nagłówka symbolu głównego.  
  
    > [!NOTE]
    >  **Ważne** wpisz w polu tylko do odczytu symbol dyrektywy znajduje się w pliku zasobów dokładnie podczas pisania. Upewnij się, że możesz wpisać nie zawiera żadnych błędów pisowni lub składni.  
  
     Użyj **dyrektywy symboli tylko do odczytu** pole, aby uwzględnić pliki z tylko definicje symbolu. Nie dołączaj definicji zasobów; w przeciwnym razie definicji zduplikowanych zasobów zostanie utworzony po zapisaniu pliku.  
  
3.  Umieść symbole podanego pliku.  
  
     Symbole w plików znajdujących się w ten sposób są oceniane w każdym otwarciu Twojego pliku zasobu, ale nie zastąpienia na dysku po zapisaniu pliku.  
  
4.  Kliknij przycisk **OK**.  
  

  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)   
 [Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)   
 [Wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)   
 [Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)