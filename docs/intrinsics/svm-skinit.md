---
title: __svm_skinit
ms.date: 11/04/2016
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 630d4b9d93802038bd00b65495bb18455b0c61a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591220"
---
# <a name="svmskinit"></a>__svm_skinit

**Microsoft Specific**

Inicjuje ładowanie i bezpiecznego oprogramowania, np. monitor maszyny wirtualnej.

## <a name="syntax"></a>Składnia

```
void __svm_skinit(
   int SLB
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`SLB`|32-bitowy adres fizyczny bajt 64K zabezpieczanie modułu ładującego bloku (SLB).|

## <a name="remarks"></a>Uwagi

`__svm_skinit` Funkcji jest odpowiednikiem `SKINIT` machine instrukcji. Ta funkcja jest częścią system zabezpieczeń, który korzysta z procesora i zaufanych Platform Module (TPM) w celu sprawdzenia i załadować zaufane oprogramowanie o nazwie jądra zabezpieczeń (SK). Monitorowanie maszyny wirtualnej znajduje się przykład jądra zabezpieczeń. System zabezpieczeń sprawdza, składniki programu załadowany w procesie inicjowania i chroni składników przed naruszeniami poprzez przerwań, uzyskiwania dostępu do urządzenia lub innego programu, jeśli komputer jest wieloprocesorowych.

`SLB` Parametr określa adres fizyczny bloku 64 KB pamięci o nazwie *zabezpieczanie modułu ładującego bloku* (SLB). SLB zawiera program o nazwie bezpiecznego modułu ładującego, która ustanawia środowisko operacyjne dla komputera, a następnie ładuje jądra zabezpieczeń.

Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" numer 24593, wersji 3.11, dokumentu w [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)