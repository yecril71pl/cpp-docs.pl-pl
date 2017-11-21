---
title: -REBASE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /rebase
dev_langs: C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05b718b20ad941764158f2de461614885b0627fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja umożliwia ustawienie adresu podstawowego dla określonych plików. Polecenia EDITBIN przypisuje nowy adres podstawowy w przestrzeni adresowej ciągłe na podstawie rozmiaru poszczególnych plików zaokrąglona do najbliższej 64 KB. Aby uzyskać szczegółowe informacje o adresach podstawowej, zobacz [adres podstawowy](../../build/reference/base-base-address.md) (/ BASE) — opcja konsolidatora.  
  
 Określ program plików wykonywalnych i bibliotek DLL w *pliki* argument w wierszu polecenia polecenia EDITBIN w kolejności, w którym mają zostać oparte. Opcjonalnie można określić jedną lub więcej *Modyfikatory*, rozdzielonych przecinkami (**,**):  
  
|Modyfikator|Akcja|  
|--------------|------------|  
|Podstawa**=***adresu*|Adres początkowy przewiduje ponowne przypisywanie adresów bazowych do plików. Określ *adres* dziesiętne lub notacji języka C. Jeśli podstawowy nie jest określony, domyślnie podstawowy adres początkowy jest 0x400000. Jeśli w dół używany jest podstawowy musi być określona, i *adres* ustawia końca zakresu adresów podstawowej.|  
|BASEFILE|Tworzy plik o nazwie COFFBASE. Pliki TXT, który jest plikiem tekstowym formatu oczekiwanego przez łącza/BASE — opcja.|  
|W DÓŁ|Określa, że polecenia EDITBIN do ponownego przypisania podstawowy adres w dół z adresu końcowego. Pliki są przekazywane w kolejności określonej z pierwszy plik znajdujący się w adresie można najwyższy pod koniec zakresu adresów. BASE należy użyć do zapewnienia wystarczającej przestrzeni adresowej używanej przez utworzenie plików z w dół. Aby ustalić przestrzeń adresowa wymaganych przez określone pliki, Uruchom polecenia EDITBIN z /REBASE plików, a następnie dodaj 64 KB wyświetlanych całkowity rozmiar.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)