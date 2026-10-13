# Guía de Rutas y Decisiones — Mizuiro Remake (みずいろ)

Guía completa de progresión de rutas y selección de heroínas para *Mizuiro Remake*.

---

## 1. Estructura y Funcionamiento del Juego

*Mizuiro Remake* se divide en dos fases narrativas claramente diferenciadas:

1. **Parte Pasado / Infancia**:
   - Es el prólogo común obligatorio en una partida nueva.
   - **Aquí se decide al 100% la ruta de la heroína.**
   - Cada decisión moldea la relación de Kenji con las chicas del vecindario. Al final de la infancia, el juego evalúa las elecciones tomadas y determina la ruta correspondiente.
   - Tras reproducirse el tema de apertura (`op.wmv`), la historia salta directamente al escenario del presente correspondiente.

2. **Parte Presente / Adolescencia**:
   - Transcurre en la etapa de instituto con la heroína fijada.
   - Las elecciones dentro de estos escenarios no cambian de heroína; se enfocan en variaciones cómicas de diálogo, escenas de vida cotidiana y obtención de CGs del álbum.

---

## 2. Mapa de Rutas

| Ruta | Heroína | Rol / Descripción |
|:---:|:---|:---|
| **1** | **早坂 日和** (Hiyori Hayasaka) | Amiga de la infancia y vecina enérgica. |
| **2** | **片瀬 雪希** (Yuki Katase) | Amiga de la infancia, dulce y reservada (Heroína principal). |
| **3 / 5** | **神津 麻美** (Asami Maeda) | Senpai carismática del instituto. |
| **4** | **小野崎 清香** (Kiyoka Onozaki) | Compañera tímida aficionada a los libros. |
| **7** | **若草 冬佳** (Fuka Wakakusa) | Profesora tutora (Fuka-sensei). |
| **8** | **進藤 むつき** (Mutsuki Shindou) | Amiga atlética y espontánea de la gorra. |
| **Extra** | **ν日和** (Nu-Hiyori) | Variante cómica secreta de Hiyori. |

---

## 3. Diagrama de Flujo del Pasado

```mermaid
flowchart TD
    Start["Inicio: Día de nieve en la infancia"] --> C1{"¿Qué hacer con el partido de fútbol?"}

    %% Rama Hiyori / Nu-Hiyori
    C1 -- "■サッカーはとりやめ<br>(Cancelar el fútbol)" --> C_Hiyo1{"¿Quedarse con Hiyori?"}
    C_Hiyo1 -- "■やっぱり日和と一緒に<br>(Quedarme con Hiyori)" --> Route_Hiyori["Ruta 早坂 日和 (Hiyori)<br>Flag = 1"]
    C_Hiyo1 -- "■それでも外は寒そうだし…<br>(Parece que hace frío fuera...)" --> C_Nu{"¿Pedírselo a Hiyori?"}
    C_Nu -- "■日和にお願いしてみる<br>(Pedírselo a Hiyori)" --> Route_Nu["Ruta secreta ν日和 (Nu-Hiyori)"]
    C_Nu -- "■やっぱり我慢する<br>(Aguantarme)" --> Route_Hiyori

    %% Rama Fútbol
    C1 -- "■それでもサッカーに行く<br>(Ir al fútbol de todos modos)" --> C2{"Tras llegar al parque..."}

    %% Subrama Mutsuki
    C2 -- "■もうすこし時間をつぶす<br>(Hacer un poco más de tiempo)" --> C_Mut{"Encuentro con Mutsuki en el parque"}
    C_Mut --> M1["■照れ隠しに謝る (Disculparme por vergüenza)"]
    M1 --> M2["■手を貸す (Echarle una mano)"]
    M2 --> M3["■連れていってあげる (Llevarla conmigo)"]
    M3 --> M4["■自分から名のる (Presentarme)"]
    M4 --> M5["■また行ってみる (Ir de nuevo)"]
    M5 --> M6["■買ってみようか (¿Compramos algo?)"]
    M6 --> Route_Mutsuki["Ruta 進藤 むつき (Mutsuki)<br>Flag = 8"]

    %% Tronco Principal (Yuki / Kiyoka / Asami / Fuka)
    C2 -- "■雪希と日和の所へ帰る<br>(Volver con Yuki e Hiyori)" --> MainCommon["Tronco Común:<br>1. ■道を説明してあげる (Explicar camino)<br>2. ■雪希に聞いてみる (Preguntar a Yuki)<br>3. ■雪希の夢 (El sueño de Yuki)"]

    MainCommon --> C3{"¿Qué hacer sobre Yuki?"}

    %% Subrama Yuki / Fuka
    C3 -- "■むかえに行ってやらないと<br>(Tengo que ir a buscarla)" --> C_YukiFuka{"¿Qué regalarle?"}
    C_YukiFuka -- "■代わりに指輪をあげるかな<br>(Regalarle un anillo en su lugar)" --> Route_Yuki["Ruta 片瀬 雪希 (Yuki)<br>Flag = 2"]
    C_YukiFuka -- "■あんなもん渡しても喜ばないだろ<br>(No se alegrará con algo así)" --> Route_Fuka["Ruta 若草 冬佳 (Fuka)<br>Flag = 7"]

    %% Subrama Kiyoka / Asami
    C3 -- "■雪希も大きくなったから大丈夫かな？<br>(Yuki ya es mayor, ¿estará bien?)" --> C_KiyoAsa1{"¿Cómo responder?"}
    C_KiyoAsa1 -- "■見てないぞ (No he mirado)" --> C_KiyoCommon["■聞き返してやる (Preguntarle)<br>■一緒に遊ぶ (Jugar juntos)"]
    C_KiyoAsa1 -- "■ばっちし (¡Perfecto!)" --> C_AsaCommon["■聞き返してやる (Preguntarle)<br>■一緒に遊ぶ (Jugar juntos)"]

    C_KiyoCommon --> C_FinalKiyo{"Petición final"}
    C_FinalKiyo -- "■軽いもんだ (Pan comido)" --> Route_Kiyoka["Ruta 小野崎 清香 (Kiyoka)<br>Flag = 4"]

    C_AsaCommon --> C_FinalAsa{"Petición final"}
    C_FinalAsa -- "■めんどくさいから嫌だ (Qué pereza, paso)" --> Route_Asami["Ruta 神津 麻美 (Asami-senpai)<br>Flag = 3 / 5"]
```

---

## 4. Guía Paso a Paso por Heroína

### 🌸 片瀬 雪希 (Yuki Katase)
> *La amiga de la infancia dulce, tranquila y devota. La ruta central de Mizuiro.*

**Pasos en la Infancia:**
1. `■それでもサッカーに行く` *(Aun así voy al fútbol)*
2. `■雪希と日和の所へ帰る` *(Volver a donde están Yuki e Hiyori)*
3. `■道を説明してあげる` *(Explicarle el camino)*
4. `■雪希に聞いてみる` *(Preguntarle a Yuki)*
5. `■雪希の夢` *(El sueño de Yuki)*
6. `■むかえに行ってやらないと` *(Tengo que ir a buscarla)*
7. `■代わりに指輪をあげるかな` *(Quizá deba regalarle un anillo en su lugar)*

---

### ☀️ 早坂 日和 (Hiyori Hayasaka)
> *La vecina y amiga de la infancia revoltosa y enérgica de Kenji.*

**Pasos en la Infancia:**
1. `■サッカーはとりやめ` *(Cancelo el partido de fútbol)*
2. `■やっぱり日和と一緒に` *(Quedarme con Hiyori después de todo)*

*(Al completar esta ruta se desbloquea el escenario especial en el menú principal).*

---

### 🧢 進藤 むつき (Mutsuki Shindou)
> *La chica atlética y extrovertida que Kenji conoce en el campo de fútbol.*

**Pasos en la Infancia:**
1. `■それでもサッカーに行く` *(Aun así voy al fútbol)*
2. `■もうすこし時間をつぶす` *(Hacer un poco más de tiempo)*
3. `■照れ隠しに謝る` *(Disculparme para disimular la vergüenza)*
4. `■手を貸す` *(Echarle una mano)*
5. `■連れていってあげる` *(Llevarla conmigo)*
6. `■自分から名のる` *(Presentarme primero)*
7. `■また行ってみる` *(Ir de nuevo)*
8. `■買ってみようか` *(¿Compramos algo?)*

---

### 📖 小野崎 清香 (Kiyoka Onozaki)
> *La chica compañera de clase con un lazo enorme.*

**Pasos en la Infancia:**
1. `■それでもサッカーに行く` *(Aun así voy al fútbol)*
2. `■雪希と日和の所へ帰る` *(Volver a donde están Yuki e Hiyori)*
3. `■道を説明してあげる` *(Explicarle el camino)*
4. `■雪希に聞いてみる` *(Preguntarle a Yuki)*
5. `■雪希の夢` *(El sueño de Yuki)*
6. `■雪希も大きくなったから大丈夫かな？` *(Yuki ya es mayor, ¿estará bien?)*
7. `■見てないぞ` *(No he mirado)*
8. `■聞き返してやる` *(Preguntarle de vuelta)*
9. `■一緒に遊ぶ` *(Jugar juntos)*
10. `■軽いもんだ` *(Pan comido)*

---

### 👑 神津 麻美 (Asami Maeda / 麻美先輩)
> *La carismática y admirada senpai del instituto.*

**Pasos en la Infancia:**
1. `■それでもサッカーに行く` *(Aun así voy al fútbol)*
2. `■雪希と日和の所へ帰る` *(Volver a donde están Yuki e Hiyori)*
3. `■道を説明してあげる` *(Explicarle el camino)*
4. `■雪希に聞いてみる` *(Preguntarle a Yuki)*
5. `■雪希の夢` *(El sueño de Yuki)*
6. `■雪希も大きくなったから大丈夫かな？` *(Yuki ya es mayor, ¿estará bien?)*
7. `■ばっちし` *(¡Perfecto! / Lo tengo todo visto)*
8. `■聞き返してやる` *(Preguntarle de vuelta)*
9. `■一緒に遊ぶ` *(Jugar juntos)*
10. `■めんどくさいから嫌だ` *(Qué pereza, paso)*

---

### ☕ 若草 冬佳 (Fuka Wakakusa / 冬佳先生)
> *La comprensiva y serena profesora tutora.*

**Pasos en la Infancia:**
1. `■それでもサッカーに行く` *(Aun así voy al fútbol)*
2. `■雪希と日和の所へ帰る` *(Volver a donde están Yuki e Hiyori)*
3. `■道を説明してあげる` *(Explicarle el camino)*
4. `■雪希に聞いてみる` *(Preguntarle a Yuki)*
5. `■雪希の夢` *(El sueño de Yuki)*
6. `■むかえに行ってやらないと` *(Tengo que ir a buscarla)*
7. `■あんなもん渡しても喜ばないだろ` *(No se va a alegrar si le doy una cosa así)*

---

### 🌀 ν日和 (Nu-Hiyori)
> *Variante cómica y alternativa de Hiyori.*

**Pasos en la Infancia:**
1. `■サッカーはとりやめ` *(Cancelo el partido de fútbol)*
2. `■それでも外は寒そうだし…` *(Aun así parece que hace frío fuera...)*
3. `■日和にお願いしてみる` *(Pedírselo a Hiyori)*

---

## 5. Contenidos Extra y Desbloqueables

- **After Story de Yuki**: Se desbloquea tras alcanzar el final de Yuki. Permite ver el epílogo y las CGs finales.
- **Escenario "Mizuiro" en Menú Principal**: Se desbloquea tras finalizar la ruta de Hiyori.
- **Staff Room (Sala del Personal)**: Accesible desde los extras tras completar el juego. El programador original Chouhata incluye comentarios y la guía de rutas oficial.
- **Historias Omake**:
  - *愛衣と雛姫* (Ai y Hinaki)
  - *愛衣と雛姫、その後* (Ai y Hinaki, después)
  - *野望* (Ambición)
