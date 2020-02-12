---
title: Stałe przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
ms.openlocfilehash: 2d304728f5bdca8f4bfb39cdb26baad984e63097
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126931"
---
# <a name="concurrency-namespace-constants-amp"></a>Stałe przestrzeni nazw współbieżności (AMP)

|||
|-|-|
|[HLSL_MAX_NUM_BUFFERS](#hlsl_max_num_buffers)|[MODULENAME_MAX_LENGTH](#modulename_max_length)|

## <a name="hlsl_max_num_buffers"></a>HLSL_MAX_NUM_BUFFERS stała

Maksymalna liczba buforów dozwolona przez program DirectX.

```cpp
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;
```

## <a name="modulename_max_length"></a>MODULENAME_MAX_LENGTH stała

Przechowuje maksymalną długość nazwy modułu. Ta wartość musi być taka sama w kompilatorze i środowisku uruchomieniowym.

```cpp
static const UINT MODULENAME_MAX_LENGTH = 1024;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
