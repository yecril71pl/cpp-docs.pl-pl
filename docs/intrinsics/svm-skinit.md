---
title: __svm_skinit
ms.date: 11/04/2016
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 199cba2623f9d8e47c08be642ec485599b87976e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026139"
---
# <a name="svmskinit"></a>__svm_skinit

**Specyficzne dla firmy Microsoft**

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

Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: System programowania,"numer 24593, wersji 3.11, dokumentu na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)