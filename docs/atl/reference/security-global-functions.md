---
title: Globalne funkcje zabezpieczeń
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326034"
---
# <a name="security-global-functions"></a>Globalne funkcje zabezpieczeń

Funkcje te zapewniają obsługę modyfikowania obiektów SID i ACL.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AtlGetDacl (AtlGetDacl)](#atlgetdacl)|Wywołaj tę funkcję, aby pobrać informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.|
|[AtlSetDacl (AtlSetDacl)](#atlsetdacl)|Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.|
|[AtlGetGroupSid (Wys.](#atlgetgroupsid)|Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.|
|[AtlSetGroupSid (Wystawięt.](#atlsetgroupsid)|Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.|
|[AtlGetOwnerSid (Identyfikator AtlGetOwnerSid)](#atlgetownersid)|Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.|
|[AtlSetOwnerSid (AtlSetOwnerSid)](#atlsetownersid)|Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.|
|[AtlGetSacl (AtlGetSacl)](#atlgetsacl)|Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.|
|[AtlSetSacl (AtlSetSacl)](#atlsetsacl)|Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.|
|[Deskryptor AtlGetSecurity](#atlgetsecuritydescriptor)|Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl (AtlGetDacl)

Wywołaj tę funkcję, aby pobrać informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, dla którego mają być pobierane informacje o zabezpieczeniach.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*pDacl (pDacl)*<br/>
Wskaźnik do obiektu DACL, który będzie zawierał pobrane informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *hObject* lub *pDacl* jest nieprawidłowy.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>AtlSetDacl (AtlSetDacl)

Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, dla którego należy ustawić informacje zabezpieczające.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*rDacl ( rDacl )*<br/>
Listy DACL zawierające nowe informacje o zabezpieczeniach.

*dwInheritanceFlowControl (Kontrola przepływu)*<br/>
Kontrola przepływu dziedziczenia. Ta wartość może wynosić 0 (wartość domyślna), PROTECTED_DACL_SECURITY_INFORMATION lub UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *hObject* jest nieprawidłowy lub jeśli *dwInheritanceFlowControl* nie jest jedną z trzech dozwolonych wartości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid (Wys.

Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, z którego mają być pobierane informacje o zabezpieczeniach.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*pSid*<br/>
Wskaźnik do `CSid` obiektu, który będzie zawierał nowe informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid (Wystawięt.

Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, dla którego należy ustawić informacje zabezpieczające.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*rSid (wyd.*<br/>
Obiekt `CSid` zawierający nowe informacje zabezpieczające.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid (Identyfikator AtlGetOwnerSid)

Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, z którego mają być pobierane informacje o zabezpieczeniach.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*pSid*<br/>
Wskaźnik do `CSid` obiektu, który będzie zawierał nowe informacje o zabezpieczeniach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid (AtlSetOwnerSid)

Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, dla którego należy ustawić informacje zabezpieczające.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*rSid (wyd.*<br/>
Obiekt `CSid` zawierający nowe informacje zabezpieczające.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>AtlGetSacl (AtlGetSacl)

Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, z którego mają być pobierane informacje o zabezpieczeniach.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*pSacl (właswoi)*<br/>
Wskaźnik do obiektu SACL, który będzie zawierał pobrane informacje o zabezpieczeniach.

*bRequestNieniesoprawne*<br/>
Jeśli true, funkcja podejmie próbę włączenia SE_SECURITY_NAME uprawnienia i przywrócić go po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli `AtlGetSacl` ma być wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnienie SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivileges* ustawić false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>AtlSetSacl (AtlSetSacl)

Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojście do obiektu, dla którego należy ustawić informacje zabezpieczające.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *hObject.*

*rSacl*<br/>
SACL zawierający nowe informacje dotyczące bezpieczeństwa.

*dwInheritanceFlowControl (Kontrola przepływu)*<br/>
Kontrola przepływu dziedziczenia. Ta wartość może wynosić 0 (wartość domyślna), PROTECTED_SACL_SECURITY_INFORMATION lub UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNieniesoprawne*<br/>
Jeśli true, funkcja podejmie próbę włączenia SE_SECURITY_NAME uprawnienia i przywrócić go po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *hObject* jest nieprawidłowy lub jeśli *dwInheritanceFlowControl* nie jest jedną z trzech dozwolonych wartości.

Jeśli `AtlSetSacl` ma być wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnienie SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivileges* ustawić false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>Deskryptor AtlGetSecurity

Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*pszObjectName*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę obiektu, z którego mają być pobierane informacje o zabezpieczeniach.

*Objecttype*<br/>
Określa wartość z [wyliczenia SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) która wskazuje typ obiektu identyfikowanego przez parametr *pszObjectName.*

*pDeptor zabezpieczeń*<br/>
Obiekt, który odbiera żądany deskryptor zabezpieczeń.

*requestedInfo*<br/>
Zestaw [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) flag bitowych wskazujących typ informacji zabezpieczających do pobrania. Ten parametr może być kombinacją następujących wartości.

*bRequestNieniesoprawne*<br/>
Jeśli true, funkcja podejmie próbę włączenia SE_SECURITY_NAME uprawnienia i przywrócić go po zakończeniu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Jeśli `AtlGetSecurityDescriptor` ma być wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnienie SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivileges* ustawić false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
