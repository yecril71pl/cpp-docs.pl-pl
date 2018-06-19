---
title: -REBASE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rebase
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a5e2b68768b01d71532c358a14c53d8a033e1ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377092"
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
|Podstawa **= *** adresu*|Adres początkowy przewiduje ponowne przypisywanie adresów bazowych do plików. Określ *adres* dziesiętne lub notacji języka C. Jeśli podstawowy nie jest określony, domyślnie podstawowy adres początkowy jest 0x400000. Jeśli w dół używany jest podstawowy musi być określona, i *adres* ustawia końca zakresu adresów podstawowej.|  
|BASEFILE|Tworzy plik o nazwie COFFBASE. Pliki TXT, który jest plikiem tekstowym formatu oczekiwanego przez łącza/BASE — opcja.|  
|W DÓŁ|Określa, że polecenia EDITBIN do ponownego przypisania podstawowy adres w dół z adresu końcowego. Pliki są przekazywane w kolejności określonej z pierwszy plik znajdujący się w adresie można najwyższy pod koniec zakresu adresów. BASE należy użyć do zapewnienia wystarczającej przestrzeni adresowej używanej przez utworzenie plików z w dół. Aby ustalić przestrzeń adresowa wymaganych przez określone pliki, Uruchom polecenia EDITBIN z /REBASE plików, a następnie dodaj 64 KB wyświetlanych całkowity rozmiar.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)