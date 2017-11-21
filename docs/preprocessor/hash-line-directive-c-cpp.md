---
title: "#<a name=\"line-directive-cc--microsoft-docs\"></a>wiersz — dyrektywa (C/C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#line'
dev_langs: C++
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41886c8107db882ad3bea5a041b529ba8bbbeed6
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="line-directive-cc"></a>#line — dyrektywa (C/C++)

Dyrektywa `#line` mówi preprocesorowi, żeby zmienił wewnętrznie przechowywany przez kompilator numer wiersza oraz nazwę pliku na podany numer wiersza i nazwę pliku.

## <a name="syntax"></a>Składnia

> **#line** *sekwencji cyfr* ["*filename*"]

## <a name="remarks"></a>Uwagi

Kompilator używa numeru wiersza i opcjonalnie nazwy pliku, aby odwoływać się do błędów znalezionych podczas kompilacji. Zazwyczaj numer wiersza odwołuje się do bieżącego wiersza wejściowego, a nazwa pliku do bieżącego pliku wejściowego. Numer wiersza jest zwiększany po przetworzeniu każdego wiersza.

*Sekwencji cyfr* wartość może być dowolnym stała liczba całkowita. Zamiana makro może zostać wykonana na tokenach przetwarzania wstępnego, ale wynik musi zostać oszacowany według poprawnej składni. *Filename* może być dowolną kombinację znaków i musi być ujęta w znaki podwójnego cudzysłowu (**""**). Jeśli *filename* jest pominięty, poprzednie filename pozostaje niezmieniona.

Możesz zmienić numer wiersza źródła i nazwę pliku, przez napisanie dyrektywy `#line`. Translator używa numeru wiersza i nazwę pliku w celu określenia wartości wstępnie zdefiniowane makra **&#95; &#95; Plik &#95; &#95;**  i **&#95; &#95; WIERSZ &#95; &#95;** . Możesz użyć tych makr, aby wstawić samoopisowe komunikaty o błędzie do tekstu programu. Aby uzyskać więcej informacji o tych wstępnie zdefiniowane makra, zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md).

**&#95; &#95; Plik &#95; &#95;**  makro rozwijany do ciągu, których zawartość jest nazwa pliku ujęta w znaki podwójnego cudzysłowu (**""**).

Jeśli zmienisz numer wiersza i nazwę pliku, kompilator zignoruje poprzednie wartości i będzie kontynuował przetwarzanie z nowymi wartościami. Dyrektywa `#line` jest zwykle używana przez generatory programu, aby spowodować, żeby komunikaty o błędach dotyczyły oryginalnego pliku źródłowego zamiast wygenerowanego programu.

Poniższe przykłady przedstawiają `#line` i **&#95; &#95; WIERSZ &#95; &#95;**  i **&#95; &#95; Plik &#95; &#95;**  makra.

W tej instrukcji numer wiersza wewnętrznych zapisanych ustawiono 151 i nazwa pliku została zmieniona na copy.c.

```cpp
#line 151 "copy.c"
```

 W tym przykładzie makro `ASSERT` używa wstępnie zdefiniowane makra **&#95; &#95; WIERSZ &#95; &#95;**  i **&#95; &#95; Plik &#95; &#95;**  do drukowania komunikat o błędzie dotyczący pliku źródłowego, jeśli dany potwierdzenie nie zostanie spełniony.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)