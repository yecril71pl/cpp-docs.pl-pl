---
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 6657921d647a23bf027a5800702527951f7f6831
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219865"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Microsoft Specific**

Inicjuje ładowanie bezpiecznego oprogramowania, takiego jak monitor maszyny wirtualnej.

## <a name="syntax"></a>Składnia

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>Parametry

*block_address*\
32-bitowy adres fizyczny 64-bitowego bloku modułu ładującego.

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `SKINIT` z instrukcją maszyny. `__svm_skinit` Ta funkcja jest częścią systemu zabezpieczeń, który używa procesora i moduł TPM (TPM) do sprawdzania i ładowania zaufanego oprogramowania, zwanego jądrem *zabezpieczeń* (SK). Przykładem jądra zabezpieczeń jest monitor maszyny wirtualnej. System zabezpieczeń weryfikuje składniki programu załadowane podczas procesu inicjowania. Chroni składniki przed naruszeniem przez przerwania, dostęp do urządzenia lub inny program, jeśli komputer jest wieloprocesorowy.

Parametr *block_address* określa adres fizyczny bloku 64 KB pamięci o nazwie *bezpieczny blok modułu ładującego (moduł* równoważenia obciążenia). Moduł równoważenia obciążenia zawiera program o nazwie *bezpiecznego modułu ładującego*. Ustanawia środowisko operacyjne dla komputera, a następnie ładuje jądro zabezpieczeń.

Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, wyszukaj frazę "Volume Architecture — ręczny wolumin 2". Programowanie systemu "w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
