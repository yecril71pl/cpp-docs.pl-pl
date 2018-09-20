---
title: Klasa Icommandtarget | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95faae4de2e9fa756a4f69f231839e19019e08fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436809"
---
# <a name="icommandtarget-interface"></a>Klasa Icommandtarget

Udostępnia kontrolkę użytkownika z interfejsem w celu odbierania poleceń od obiektu źródła polecenia.

## <a name="syntax"></a>Składnia

```
interface class ICommandTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|Inicjuje obiekt docelowy polecenia.|

## <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacja poleceń interfejsu użytkownika wiadomości do formantu użytkownika, aby zezwalała na obsługę jego poleceń MFC (na przykład ramek elementów menu i przycisków paska narzędzi). Implementując `ICommandTarget`, podać odwołanie do formantu użytkownika [ICommandSource](../../mfc/reference/icommandsource-interface.md) obiektu.

Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

##  <a name="initialize"></a> ICommandTarget::Initialize

Inicjuje obiekt docelowy polecenia.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Dojście do obiektu źródła polecenia.

### <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC CWinFormsView kieruje polecenia i komunikaty interfejs użytkownika polecenia aktualizacji do formantu użytkownika, aby zezwolić na obsługę jego poleceń MFC.

Ta metoda inicjuje obiekt docelowy polecenia i kojarzy ją z cmdSource obiektu źródłowego określonego polecenia. Powinien zostać wywołany w implementacji klasy formantu użytkownika. Podczas inicjowania należy zarejestrować programy obsługi poleceń, za pomocą obiektu źródła polecenia przez ICommandSource::AddCommandHandler wywołujący w implementacji inicjowania. Zobacz porady: Dodawanie routingu poleceń do kontrolki formularzy Windows przykład jak to zrobić za pomocą inicjowania.

## <a name="see-also"></a>Zobacz też

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Klasa ICommandSource](../../mfc/reference/icommandsource-interface.md)



