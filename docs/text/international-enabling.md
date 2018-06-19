---
title: Włączanie internacjonalizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f4edcae610f17409c319c7b4bd39dc137e1211e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858705"
---
# <a name="international-enabling"></a>Włączanie internacjonalizacji
Najbardziej tradycyjnych kodu C i C++ sprawia, że założenia dotyczące znaków i ciąg, które działa dobrze w aplikacjach międzynarodowych. Gdy zarówno MFC, jak i biblioteki wykonawczej obsługują standardu Unicode i MBCS, jest nadal pracy należy wykonać. Pomocny, w tej sekcji wyjaśniono znaczenie "Włączanie internacjonalizacji" w programie Visual C++:  
  
-   Zarówno Unicode i MBCS są włączane przy użyciu przenośne typy danych w listy parametrów funkcji MFC i zwracanych typów. Te typy warunkowo są definiowane w odpowiedni sposób, w zależności od tego, czy kompilację definiuje symbol **_unicode —** lub symbol **_MBCS** (co oznacza DBCS). Różne rodzaje bibliotek MFC automatycznie są połączone z aplikacji, w zależności od tego, która z tych dwóch symboli definiuje kompilacji.  
  
-   Kod biblioteki klas używa przenośne funkcje wykonawcze języka i inny sposób, aby zapewnić poprawne zachowanie Unicode i MBCS.  
  
-   Możesz nadal obsługiwać niektóre rodzaje zadań internacjonalizacji w kodzie:  
  
    -   Funkcji tej samej przenośne środowiska wykonawczego wchodzące przenośnego albo środowisku MFC.  
  
    -   Wprowadź ciągi literału i znaki przenośnego albo środowisku przy użyciu **_t —** makra. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
    -   Podczas analizowania parametrów w obszarze MBCS wymaga wykonania kroków. W obszarze Unicode nie są wymagane następujące środki ostrożności. Aby uzyskać więcej informacji, zobacz [porady programowania MBCS](../text/mbcs-programming-tips.md).  
  
    -   Zajmie się jeśli mieszać ANSI (8-bitowych) i znaki Unicode (16-bitowy) w aplikacji. Można użyć znaków ANSI niektórych części programu i znaki Unicode w innym, ale nie można mieszać je w tych samych parametrach.  
  
    -   Nie ciągów nie kodowane w aplikacji. Zamiast tego należy je STRINGTABLE zasobów przez dodanie ich do pliku .rc aplikacji. Następnie można lokalizować aplikacji bez konieczności zmiany kodu źródłowego lub ponownej kompilacji. Aby uzyskać więcej informacji o zasobach STRINGTABLE, zobacz [edytor ciągów](../windows/string-editor.md).  
  
> [!NOTE]
>  Zestawy znaków Europejskiej i MBCS ma niektórych znaków, takich jak akcentowanych z kodów znaków jest większa niż 0x80. Ponieważ większość kodu używa podpisem znaków, te znaki, które są większe niż 0x80 są znakiem, po konwersji na `int`. Jest to problem dotyczący indeksowanie tablicy, ponieważ indeksy znakiem znaków jest ujemna, poza tablicy. Języków, które używają MBCS, takich jak japoński, również są unikatowe. Ponieważ znak może składać się z 1 lub 2 bajty, należy zawsze manipulować zarówno bajtów w tym samym czasie.  
  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Strategie internacjonalizacji](../text/internationalization-strategies.md)