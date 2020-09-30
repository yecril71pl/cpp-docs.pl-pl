---
title: Używanie typów danych TCHAR.H z _MBCS
description: Omówienie sposobu mapowania procedur tekstowych środowiska uruchomieniowego języka Microsoft C w przypadku korzystania z używanie TCHAR. H typy danych ze stałą wielobajtową _MBCS.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
ms.openlocfilehash: 001f745c03e4e0c0090e40c00c5394397028659f
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589955"
---
# <a name="using-tcharh-data-types-with-_mbcs"></a>Używanie typów danych TCHAR.H z _MBCS

**Specyficzne dla firmy Microsoft**

Jak tabela mapowań procedury tekstu ogólnego wskazuje (zobacz [mapowania tekstu ogólnego](../c-runtime-library/generic-text-mappings.md)), gdy jest zdefiniowana stała manifestu **_MBCS** , dana procedura tekstu ogólnego mapuje do jednego z następujących rodzajów procedur:

- Procedura SBCS, która obsługuje odpowiednio bajty wielobajtowe, znaki i ciągi. W tym przypadku argumenty ciągu powinny być typu **char&#42;**. Na przykład **_tprintf** Maps **printf**; argumenty ciągu do **printf** są typu **char&#42;**. Jeśli używasz typu danych **_TCHAR** Generic-Text dla typów ciągów, formalne i rzeczywiste typy parametrów dla **printf** match, ponieważ **_TCHAR&#42;** mapy do **char&#42;**.

- Procedura specyficzna dla MBCS. W takim przypadku argumenty ciągu mają być typu __unsigned char&#42;__. Na przykład **_tcsrev** mapuje do **_mbsrev**, która oczekuje i zwraca ciąg typu __char bez znaku&#42;__. Ponownie, jeśli używasz typu danych **_TCHAR** rodzajowego dla typów ciągów, występuje konflikt typu, ponieważ **_TCHAR** mapuje do typu **`char`** .

Poniżej przedstawiono trzy rozwiązania uniemożliwiające konflikt tego typu (oraz ostrzeżenia kompilatora C lub błędy kompilatora języka C++, które byłyby wynikiem):

- Użyj zachowania domyślnego. Używanie TCHAR. H zawiera prototypy procedury tekstu ogólnego dla procedur w bibliotekach czasu wykonywania, jak w poniższym przykładzie.

   ```C
   char *_tcsrev(char *);
   ```

   W domyślnym przypadku prototyp **_tcsrev** mapowania do **_mbsrev** za pomocą thunk w libc. LIB. Spowoduje to zmianę typów **_mbsrev** przychodzących parametrów i wychodzącej wartości zwracanej z **_TCHAR &#42;** (na przykład **char &#42;**) do **niepodpisanego znaku &#42;**. Ta metoda zapewnia Dopasowywanie typów, gdy używasz **_TCHAR**, ale jest stosunkowo niska z powodu obciążenia wywołania funkcji.

- Użyj funkcji tworzenia i wykreślania w kodzie następujących instrukcji preprocesora.

   ```C
   #define _USE_INLINING
   ```

   Ta metoda powoduje, że funkcja wbudowana thunk, dostępna w używanie TCHAR. H, aby zmapować procedurę tekstu ogólnego bezpośrednio do odpowiedniej procedury MBCS. Poniższy fragment kodu z używanie TCHAR. H zawiera przykład tego, jak to zrobić.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   Jeśli możesz użyć funkcji tworzenia konspektu, jest to najlepsze rozwiązanie, ponieważ gwarantuje ono zgodność typów i nie ma dodatkowego kosztu czasu.

- Użyj "bezpośredniego mapowania", dołączając następujące instrukcje preprocesora w kodzie.

   ```C
   #define _MB_MAP_DIRECT
   ```

   Takie podejście zapewnia szybką alternatywę, jeśli nie chcesz używać zachowania domyślnego lub nie można użyć funkcji tworzenia konspektu. Makro mapuje procedurę tekstu ogólnego na wersję MBCS procedury, jak w poniższym przykładzie z używanie TCHAR. H.

   ```C
   #define _tcschr _mbschr
   ```

W przypadku podjęcia tego podejścia należy zachować ostrożność, aby zapewnić, że odpowiednie typy danych są używane dla argumentów ciągów i wartości zwracanych przez ciąg. Można użyć rzutowania typu, aby upewnić się, że odpowiedni typ jest zgodny lub można użyć **_TXCHAR** typu danych rodzajowych. **_TXCHAR** mapuje do typu **`char`** w kodzie SBCS, ale mapuje do typu **`unsigned char`** w kodzie MBCS. Aby uzyskać więcej informacji na temat makr tekstu ogólnego, zobacz [Mapowanie tekstu ogólnego](../c-runtime-library/generic-text-mappings.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Międzynarodowe](../c-runtime-library/internationalization.md)\
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
