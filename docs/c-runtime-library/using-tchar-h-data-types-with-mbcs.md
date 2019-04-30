---
title: Używanie typów danych TCHAR.H z _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
ms.openlocfilehash: b86cbc6d99cbc6969536934c1583ba5207a53629
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377900"
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Używanie typów danych TCHAR.H z _MBCS

**Microsoft Specific**

Jak wskazuje tabeli mapowania procedur zwykłego tekstu (zobacz [mapowania typ ogólny-tekst](../c-runtime-library/generic-text-mappings.md)), gdy stała manifestu **_MBCS** jest zdefiniowany, danej procedury zwykłego tekstu mapuje do jednej z następujących rodzajów programu procedury:

- Procedury SBCS, która obsługuje wielobajtowych bajtów, znaków i ciągów, odpowiednio. W tym przypadku powinny być typu argumenty typu string **char&#42;**. Na przykład **_tprintf —** mapuje **printf**; argumentów ciągów **printf** typu **char&#42;**. Jeśli używasz **_tchar —** typ danych — zwykły tekst dla ciągu typy, typy formalnego i rzeczywistego parametru dla **printf** zgodny, ponieważ **_tchar —&#42;**  mapuje **char&#42;**.

- Procedury specyficzne dla MBCS. W tym przypadku powinny być typu argumenty typu string __unsigned char&#42;__. Na przykład **_tcsrev —** mapuje **_mbsrev —**, który oczekuje, że i zwraca ciąg typu __unsigned char&#42;__. Ponownie Jeśli używasz **_tchar —** ma typ danych — zwykły tekst dla swojego typu string jest potencjalny konflikt typu **_tchar —** mapy na typ **char**.

Poniżej przedstawiono trzy rozwiązania do zapobiegania ten konflikt typu (i ostrzeżenia kompilatora C lub C++ błędy kompilatora, które umożliwiałyby):

- Użyj zachowania domyślnego. TCHAR. H udostępnia prototypy procedur zwykłego tekstu dla procedur w bibliotekach wykonawczych, jak w poniższym przykładzie.

   ```C
   char *_tcsrev(char *);
   ```

   W przypadku domyślnej prototypu **_tcsrev —** mapuje **_mbsrev —** za pośrednictwem osadzony w LIBC. LIB. Spowoduje to zmianę typów **_mbsrev —** parametry przychodzące i wychodzące zwracają wartość z **_tchar — &#42;**  (takie jak **char &#42;** ) do **unsigned char &#42;**. Ta metoda zapewnia typ dopasowania, gdy używasz **_tchar —**, ale jest stosunkowo powolne, ze względu na obciążenie wywołania funkcji.

- Aby użyć funkcji wbudowanie, zawierające następującą instrukcję preprocesora w kodzie.

   ```C
   #define _USE_INLINING
   ```

   Ta metoda powoduje, że thunk funkcji wbudowanych, podany w TCHAR. Godz., procedura — zwykły tekst bezpośrednio mapować do odpowiedniej procedury MBCS. Poniższy fragment kodu z TCHAR. H przykład jak to zrobić.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   Jeśli użyjesz wstawienia, zrównoważenia jest najlepszym rozwiązaniem, ponieważ gwarantuje to typ dopasowania i ma koszt nie dodatkowego czasu.

- Użyj "bezpośredniego mapowania", zawierające następującą instrukcję preprocesora w kodzie.

   ```C
   #define _MB_MAP_DIRECT
   ```

   To podejście oferuje szybkie alternatywna, jeśli nie mają być używane domyślne zachowanie lub nie można użyć ze śródwierszowaniem. Powoduje procedury zwykłego tekstu mają być mapowane przez makro bezpośrednio do wersji MBCS standardowego, jak w poniższym przykładzie z TCHAR. H.

   ```C
   #define _tcschr _mbschr
   ```

W przypadku zastosowania tego podejścia należy uważać, aby upewnić się, że odpowiedni typ danych są używane argumenty typu string i zwracane wartości ciągu. Rzutowanie typów można użyć do zapewnienia odpowiedniego typu dopasowania lub skorzystać z **_txchar —** typu danych — zwykły tekst. **_Txchar —** mapy na typ **char** SBCS kodu, ale mapy na typ **unsigned char** MBCS kodu. Aby uzyskać więcej informacji na temat makra zwykłego tekstu, zobacz [mapowania typ ogólny-tekst](../c-runtime-library/generic-text-mappings.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
