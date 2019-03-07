---
title: /REBASE
ms.date: 11/04/2016
f1_keywords:
- /rebase
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
ms.openlocfilehash: f0b581dfc116e25228a9aa9133c4de027e194799
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422042"
---
# <a name="rebase"></a>/REBASE

```
/REBASE[:modifiers]
```

## <a name="remarks"></a>Uwagi

Ta opcja ustawia adres podstawowy dla określonych plików. EDITBIN przypisuje nowe adresy podstawowego przestrzeni adresowej ciągłych zgodnie z rozmiarem każdego pliku, zaokrąglony do najbliższej 64 KB. Aby uzyskać szczegółowe informacje o adresach podstawowej, zobacz [adres bazowy](../../build/reference/base-base-address.md) (/ BASE) — opcja konsolidatora.

Określ pliki wykonywalne i bibliotek DLL w programie *pliki* argument w wierszu polecenia EDITBIN w kolejności, w których są one oparte. Opcjonalnie można określić co najmniej jeden *Modyfikatory*, rozdzielonych przecinkami (**,**):

|Modyfikator|Akcja|
|--------------|------------|
|**BASE=**<em>address</em>|Ponowne przypisywanie adresów bazowych w plikach udostępnia adres początkowy. Określ *adres* w wartości dziesiętne lub notacji języka C. Jeśli podstawowy nie jest określony, domyślny początkowy adres podstawowy jest 0x400000. Jeśli w dół używany jest podstawowy musi być określona, i *adres* Określa koniec zakresu adresów bazowych.|
|**BASEFILE**|Tworzy plik o nazwie COFFBASE. TXT, który jest plikiem tekstowym formatu oczekiwanego przez łącza/BASE — opcja.|
|**W DÓŁ**|Informuje o tym polecenia EDITBIN do ponownego przypisania podstawowych adresów w dół z adresu końcowego. Pliki są przypisane w kolejności określonej za pomocą pierwszego pliku znajduje się w najwyższym możliwego adresu pod koniec zakresu adresów. PODSTAWOWY musi można używać z w dół, aby zapewnić wystarczającą przestrzeń adresową dla bazowanie pliki. Aby określić przestrzeń adresowa wymagane przez określone pliki, uruchomić polecenia EDITBIN z /REBASE w systemie plików i Dodaj 64 KB do wyświetlanych całkowity rozmiar.|

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](../../build/reference/editbin-options.md)
