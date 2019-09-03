---
title: strict_gs_check, pragma
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 0b66e87f2280c923d05103fccfcbbc8d32daf3fd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216586"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check, pragma

Ta pragma zapewnia ulepszone sprawdzanie zabezpieczeń.

## <a name="syntax"></a>Składnia

> **#pragma strict_gs_check (** [ **push,** ] { **on** | **off** } **)** \
> **#pragma strict_gs_check (pop)**

## <a name="remarks"></a>Uwagi

Instruuje kompilator, aby wstawia losowo plik cookie w stosie funkcji, aby ułatwić wykrycie niektórych kategorii przepełnienia buforu opartego na stosie. Domyślnie opcja kompilatora `/GS` (sprawdzanie zabezpieczeń bufora) nie wstawia pliku cookie dla wszystkich funkcji. Aby uzyskać więcej informacji, zobacz [/GS (sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md).

Kompiluj przy użyciu `/GS` , aby włączyć **strict_gs_check**.

Użyj tej dyrektywy pragma w modułach kodu, które są narażone na potencjalnie szkodliwe dane. **strict_gs_check** to agresywna pragma, która jest stosowana do funkcji, które mogą nie wymagać tej obrony, ale jest zoptymalizowana, aby zminimalizować jej wpływ na wydajność wynikowej aplikacji.

Nawet w przypadku korzystania z tej dyrektywy pragma należy dążyć do pisania bezpiecznego kodu. Oznacza to, że kod nie ma przekroczeń buforu. **strict_gs_check** może chronić aplikację przed przekroczeniem buforów, które pozostaną w kodzie.

## <a name="example"></a>Przykład

W tym przykładzie przepełnienie buforu występuje, gdy kopiujemy tablicę do tablicy lokalnej. Podczas kompilowania tego kodu przy `/GS`użyciu programu żaden plik cookie nie zostanie wstawiony w stosie, ponieważ typ danych tablicy jest wskaźnikiem. Dodanie dyrektywy pragma **strict_gs_check** wymusza umieszczenie pliku cookie stosu w stosie funkcji.

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

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS (sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md)
