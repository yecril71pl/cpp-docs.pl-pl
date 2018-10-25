---
title: strict_gs_check | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs:
- C++
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d78a4d249852b730d80054b62a06699f50356b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067282"
---
# <a name="strictgscheck"></a>strict_gs_check

Ta dyrektywa pragma zapewnia sprawdzanie zwiększone zabezpieczenia.

## <a name="syntax"></a>Składnia

```
#pragma strict_gs_check([push,] on )
#pragma strict_gs_check([push,] off )
#pragma strict_gs_check(pop)
```

## <a name="remarks"></a>Uwagi

Instruuje kompilator, aby wstawić osiągnięciem losowego pliku cookie stosu funkcji w celu wykrycia niektóre kategorie przepełnienie buforu opartego na stosie. Domyślnie `/GS` (Sprawdzanie zabezpieczeń bufora) — opcja kompilatora nie wstawia plik cookie dla wszystkich funkcji. Aby uzyskać więcej informacji, zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md).

Należy skompilować z `/GS` (Sprawdzanie zabezpieczeń buforu) umożliwiające **strict_gs_check**.

Użyj tej pragmie w moduły kodu, które są widoczne dla danych potencjalnie szkodliwe. Ta dyrektywa pragma jest bardzo atrakcyjnych i jest stosowane do funkcji, które nie wymagają tego obrony, ale jest zoptymalizowany, aby zminimalizować jej wpływ na wydajność aplikacji wynikowe.

Nawet w przypadku używania tej pragmie powinien wszelkich starań, aby pisać bezpieczny kod. Oznacza to upewnij się, że Twój kod nie przepełnienia buforu. **strict_gs_check** może chronić aplikację przed przepełnienia buforu, które pozostają w kodzie.

## <a name="example"></a>Przykład

W poniższym kodzie przepełnienie buforu występuje, gdy firma Microsoft kopiowania tablicy do lokalnej tablicy. Gdy kompilujesz ten kod, za pomocą `/GS`, pliki cookie nie dodaje się na stosie, ponieważ typ danych tablicy jest wskaźnikiem. Dodawanie **strict_gs_check** pragma wymusza pliku cookie stosu w stos funkcji.

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // *** This buffer is subject to being overrun!! ***
    void *pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md)