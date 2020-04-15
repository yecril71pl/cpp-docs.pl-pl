---
title: Klasa CWaitCursor
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 48ef8f9c965f54deafcc62451639f8c31021e900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373175"
---
# <a name="cwaitcursor-class"></a>Klasa CWaitCursor

Zapewnia jednowierszowy sposób wyświetlania kursora oczekiwania, który jest zwykle wyświetlany jako klepsydra, podczas wykonywania długotrwałej operacji.

## <a name="syntax"></a>Składnia

```
class CWaitCursor
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Konstruuje `CWaitCursor` obiekt i wyświetla kursor oczekiwania.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWaitCursor::Przywróć](#restore)|Przywraca kursor oczekiwania po jego zmianie.|

## <a name="remarks"></a>Uwagi

`CWaitCursor`nie ma klasy podstawowej.

Dobre praktyki programowania systemu Windows wymagają wyświetlania kursora oczekiwania za każdym razem, gdy wykonujesz operację, która zajmuje zauważalną ilość czasu.

Aby wyświetlić kursor oczekiwania, `CWaitCursor` wystarczy zdefiniować zmienną przed kodem, który wykonuje długotrwałą operację. Konstruktor obiektu automatycznie powoduje, że kursor oczekiwania ma być wyświetlany.

Gdy obiekt wykracza poza zakres (na końcu bloku, `CWaitCursor` w którym obiekt jest zadeklarowany), jego destruktor ustawia kursor do poprzedniego kursora. Innymi słowy obiekt wykonuje niezbędne oczyszczanie automatycznie.

> [!NOTE]
> Ze względu na to, jak działają `CWaitCursor` ich konstruktorzy i destruktory, obiekty są zawsze deklarowane jako zmienne lokalne — nigdy nie są deklarowane jako zmienne globalne ani nie są przydzielane z **nowymi**.

Jeśli wykonasz operację, która może spowodować zmianę kursora, na przykład wyświetlanie okna komunikatu lub okna dialogowego, należy wywołać funkcję [przywróć](#restore) element członkowski, aby przywrócić kursor oczekiwania. Jest w porządku, aby wywołać `Restore` nawet wtedy, gdy kursor oczekiwania jest obecnie wyświetlany.

Innym sposobem wyświetlania kursora oczekiwania jest użycie kombinacji [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor), a być może [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Jednak `CWaitCursor` jest łatwiejszy w użyciu, ponieważ nie trzeba ustawić kursor do poprzedniego kursora, gdy skończysz z długotrwałą operacją.

> [!NOTE]
> MFC ustawia i przywraca kursor za pomocą funkcji wirtualnej [CWinApp::DoWaitCursor.](../../mfc/reference/cwinapp-class.md#dowaitcursor) Tę funkcję można zastąpić, aby zapewnić zachowanie niestandardowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CWaitCursor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

Aby wyświetlić kursor oczekiwania, `CWaitCursor` wystarczy zadeklarować obiekt przed kodem, który wykonuje długotrwałą operację.

```
CWaitCursor();
```

### <a name="remarks"></a>Uwagi

Konstruktor automatycznie powoduje, że kursor oczekiwania mają być wyświetlane.

Gdy obiekt wykracza poza zakres (na końcu bloku, `CWaitCursor` w którym obiekt jest zadeklarowany), jego destruktor ustawia kursor do poprzedniego kursora. Innymi słowy obiekt wykonuje niezbędne oczyszczanie automatycznie.

Można skorzystać z faktu, że destruktor jest wywoływany na końcu bloku (który może być przed końcem funkcji), aby kursor oczekiwania aktywny tylko w części funkcji. Ta technika jest pokazana w drugim przykładzie poniżej.

> [!NOTE]
> Ze względu na to, jak działają `CWaitCursor` ich konstruktorzy i destruktory, obiekty są zawsze deklarowane jako zmienne lokalne — nigdy nie są deklarowane jako zmienne globalne, ani nie są przydzielane z **nowymi**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor::Przywróć

Aby przywrócić kursor oczekiwania, należy wywołać tę funkcję po wykonaniu operacji, takiej jak wyświetlanie okna komunikatu lub okna dialogowego, które może zmienić kursor oczekiwania na inny kursor.

```
void Restore();
```

### <a name="remarks"></a>Uwagi

Jest OK, `Restore` aby wywołać nawet wtedy, gdy kursor oczekiwania jest aktualnie wyświetlany.

Jeśli trzeba przywrócić kursor oczekiwania w funkcji innej niż ta, `CWaitCursor` w której obiekt jest zadeklarowany, można wywołać [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Jak: Zmienianie kursora myszy w aplikacji klasy Microsoft Foundation](https://go.microsoft.com/fwlink/p/?linkid=128044)
