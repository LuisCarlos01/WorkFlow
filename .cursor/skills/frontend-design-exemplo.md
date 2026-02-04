---
name: frontend-design
description: Skill para criacao de interfaces frontend modernas e profissionais. Utiliza quando o usuario precisa criar landing pages, dashboards, estilizar interfaces existentes ou desenvolver componentes UI. Aplica principios de design system, hierarquia visual e mobile-first. Keywords: frontend, design, landing page, dashboard, UI, UX, componentes, tailwind, react.
---

# Frontend Design Skill

## Quando Usar Esta Skill

- Criar landing pages
- Desenvolver componentes React/Vue/Svelte (de acordo com o projeto)
- Estilizar interfaces existentes
- Criar Dashboards
- Implementar design systems
- Refatorar UI para melhor UX

## Instrucoes

### 1. Sempre Comecar com Design System

Antes de codar, definir:

- **Paleta de cores** (Maximo 5 cores)
  - Primary, Secondary, Accent, Background, Text
- **Tipografia** (2 fontes no maximo)
  - Headings: fonte display/bold
  - Body: fonte legivel/regular
- **Espacamento** (usar escala consistente)
  - Base: 4, 8, 16, 24, 32, 48, 64px

### 2. Evitar Cliches de IA

❌ **NAO usar:**
- Gradientes genericos (purple-to-pink sem proposito)
- Bordas arredondadas excessivas em tudo
- Sombras drop-shadow gigantes
- Ilustracoes 3D genericas
- "Lorem ipsum" sem contexto

✅ **USAR:**
- Cores da marca com proposito
- Hierarquia visual clara
- Espacamento consistente
- Tipografia com contraste
- Conteudo real ou placeholder relevante

### 3. Mobile First

Sempre comecar pelo mobile e expandir para desktop:

1. Estruturar layout mobile (< 640px)
2. Adicionar breakpoints tablet (md: 768px)
3. Finalizar com desktop (lg: 1024px+)

### 4. Acessibilidade Basica

- Contraste minimo 4.5:1 para texto
- Focus states visiveis
- Alt text em imagens
- Semantic HTML (header, main, nav, footer)

## Regras

✅ Usar variaveis CSS ou Tailwind config para cores
✅ Componentes reutilizaveis e compostos
✅ Animacoes sutis (max 300ms)
✅ Lazy loading para imagens
✅ Skeleton loaders para estados de loading

❌ Nao usar !important
❌ Nao hardcodar cores inline
❌ Nao criar componentes monoliticos
❌ Nao ignorar estados (hover, focus, disabled)

---

## Exemplos (Few-Shot Prompting)

### Exemplo 1: Hero Section - Landing Page

**Entrada do usuario:**
```
Crie uma hero section moderna para uma landing page de produto SaaS
```

**Resposta esperada:**

```tsx
// Hero.tsx - Design inspirado em Awwwards/21st.dev
import { Button } from "@/components/ui/button";
import { Badge } from "@/components/ui/badge";
import { ArrowRight, Play } from "lucide-react";

export function Hero() {
  return (
    <section className="relative min-h-screen flex items-center justify-center overflow-hidden">
      {/* Background com gradient sutil */}
      <div className="absolute inset-0 bg-gradient-to-b from-slate-50 to-white dark:from-slate-950 dark:to-slate-900" />
      
      {/* Grid pattern decorativo */}
      <div 
        className="absolute inset-0 opacity-[0.02]"
        style={{
          backgroundImage: `url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23000000' fill-opacity='1'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E")`
        }}
      />

      <div className="relative z-10 container mx-auto px-4 py-20">
        <div className="max-w-4xl mx-auto text-center space-y-8">
          {/* Badge de destaque */}
          <Badge 
            variant="secondary" 
            className="px-4 py-2 text-sm font-medium bg-primary/10 text-primary border-0"
          >
            ✨ Novo: Integracao com IA disponivel
          </Badge>

          {/* Headline principal */}
          <h1 className="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold tracking-tight text-slate-900 dark:text-white">
            Transforme suas ideias em{" "}
            <span className="text-primary">produtos reais</span>
          </h1>

          {/* Subheadline */}
          <p className="text-lg sm:text-xl text-slate-600 dark:text-slate-400 max-w-2xl mx-auto leading-relaxed">
            A plataforma completa para times que querem construir, lancar e escalar 
            produtos digitais com velocidade e qualidade.
          </p>

          {/* CTAs */}
          <div className="flex flex-col sm:flex-row items-center justify-center gap-4 pt-4">
            <Button size="lg" className="w-full sm:w-auto px-8 py-6 text-base">
              Comecar gratuitamente
              <ArrowRight className="ml-2 h-4 w-4" />
            </Button>
            
            <Button 
              variant="outline" 
              size="lg" 
              className="w-full sm:w-auto px-8 py-6 text-base"
            >
              <Play className="mr-2 h-4 w-4" />
              Ver demo
            </Button>
          </div>

          {/* Social proof */}
          <div className="pt-8 flex flex-col items-center gap-4">
            <div className="flex -space-x-2">
              {[1, 2, 3, 4, 5].map((i) => (
                <div
                  key={i}
                  className="w-10 h-10 rounded-full border-2 border-white dark:border-slate-900 bg-slate-200 dark:bg-slate-700"
                />
              ))}
            </div>
            <p className="text-sm text-slate-600 dark:text-slate-400">
              <span className="font-semibold text-slate-900 dark:text-white">2.500+</span>{" "}
              times ja estao usando
            </p>
          </div>
        </div>
      </div>
    </section>
  );
}
```

---

### Exemplo 2: Feature Section com Cards

**Entrada do usuario:**
```
Crie uma secao de features com cards para mostrar beneficios do produto
```

**Resposta esperada:**

```tsx
// Features.tsx
import { 
  Zap, 
  Shield, 
  BarChart3, 
  Users, 
  Clock, 
  Sparkles 
} from "lucide-react";

const features = [
  {
    icon: Zap,
    title: "Rapido como um raio",
    description: "Deploy em segundos com nossa infraestrutura otimizada para performance."
  },
  {
    icon: Shield,
    title: "Seguranca primeiro",
    description: "Criptografia de ponta a ponta e conformidade com LGPD e GDPR."
  },
  {
    icon: BarChart3,
    title: "Analytics em tempo real",
    description: "Dashboards interativos para acompanhar metricas que importam."
  },
  {
    icon: Users,
    title: "Colaboracao sem atrito",
    description: "Trabalhe em equipe com permissoes granulares e historico completo."
  },
  {
    icon: Clock,
    title: "Automacoes inteligentes",
    description: "Configure workflows que economizam horas do seu time toda semana."
  },
  {
    icon: Sparkles,
    title: "IA integrada",
    description: "Sugestoes automaticas e insights baseados nos seus dados."
  }
];

export function Features() {
  return (
    <section className="py-24 bg-white dark:bg-slate-950">
      <div className="container mx-auto px-4">
        {/* Header da secao */}
        <div className="max-w-3xl mx-auto text-center mb-16">
          <p className="text-sm font-semibold text-primary mb-3 uppercase tracking-wider">
            Recursos
          </p>
          <h2 className="text-3xl sm:text-4xl font-bold text-slate-900 dark:text-white mb-4">
            Tudo que voce precisa em um so lugar
          </h2>
          <p className="text-lg text-slate-600 dark:text-slate-400">
            Ferramentas poderosas para cada etapa do seu fluxo de trabalho.
          </p>
        </div>

        {/* Grid de features */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {features.map((feature, index) => (
            <div
              key={index}
              className="group relative p-6 rounded-2xl border border-slate-200 dark:border-slate-800 bg-slate-50/50 dark:bg-slate-900/50 hover:border-primary/50 hover:bg-white dark:hover:bg-slate-900 transition-all duration-300"
            >
              {/* Icone */}
              <div className="w-12 h-12 rounded-xl bg-primary/10 flex items-center justify-center mb-4 group-hover:bg-primary/20 transition-colors">
                <feature.icon className="w-6 h-6 text-primary" />
              </div>

              {/* Conteudo */}
              <h3 className="text-lg font-semibold text-slate-900 dark:text-white mb-2">
                {feature.title}
              </h3>
              <p className="text-slate-600 dark:text-slate-400 leading-relaxed">
                {feature.description}
              </p>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}
```

---

### Exemplo 3: Dashboard Card com Metricas

**Entrada do usuario:**
```
Crie um card de dashboard para mostrar metricas de vendas
```

**Resposta esperada:**

```tsx
// MetricCard.tsx
import { ArrowUpRight, ArrowDownRight, TrendingUp } from "lucide-react";
import { cn } from "@/lib/utils";

interface MetricCardProps {
  title: string;
  value: string;
  change: number;
  changeLabel: string;
  icon?: React.ReactNode;
}

export function MetricCard({ 
  title, 
  value, 
  change, 
  changeLabel,
  icon 
}: MetricCardProps) {
  const isPositive = change >= 0;

  return (
    <div className="relative p-6 rounded-xl border border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-950 overflow-hidden">
      {/* Background decorativo */}
      <div className="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-primary/5 to-transparent rounded-full -translate-y-1/2 translate-x-1/2" />

      <div className="relative space-y-4">
        {/* Header */}
        <div className="flex items-center justify-between">
          <p className="text-sm font-medium text-slate-600 dark:text-slate-400">
            {title}
          </p>
          {icon && (
            <div className="w-8 h-8 rounded-lg bg-primary/10 flex items-center justify-center">
              {icon}
            </div>
          )}
        </div>

        {/* Valor principal */}
        <div className="space-y-1">
          <p className="text-3xl font-bold text-slate-900 dark:text-white tracking-tight">
            {value}
          </p>
          
          {/* Indicador de mudanca */}
          <div className="flex items-center gap-2">
            <span
              className={cn(
                "inline-flex items-center px-2 py-0.5 rounded-full text-xs font-medium",
                isPositive 
                  ? "bg-emerald-100 text-emerald-700 dark:bg-emerald-900/30 dark:text-emerald-400" 
                  : "bg-red-100 text-red-700 dark:bg-red-900/30 dark:text-red-400"
              )}
            >
              {isPositive ? (
                <ArrowUpRight className="w-3 h-3 mr-0.5" />
              ) : (
                <ArrowDownRight className="w-3 h-3 mr-0.5" />
              )}
              {Math.abs(change)}%
            </span>
            <span className="text-xs text-slate-500 dark:text-slate-500">
              {changeLabel}
            </span>
          </div>
        </div>
      </div>
    </div>
  );
}

// Uso:
// <MetricCard 
//   title="Receita Total" 
//   value="R$ 45.231,89" 
//   change={12.5} 
//   changeLabel="vs mes anterior"
//   icon={<TrendingUp className="w-4 h-4 text-primary" />}
// />
```

---

### Exemplo 4: Pricing Section

**Entrada do usuario:**
```
Crie uma secao de precos com 3 planos
```

**Resposta esperada:**

```tsx
// Pricing.tsx
import { Button } from "@/components/ui/button";
import { Check } from "lucide-react";
import { cn } from "@/lib/utils";

const plans = [
  {
    name: "Starter",
    description: "Para projetos pessoais",
    price: "Gratis",
    priceDetail: "para sempre",
    features: [
      "Ate 3 projetos",
      "1GB de armazenamento",
      "Suporte por email",
      "Analytics basico"
    ],
    cta: "Comecar gratis",
    highlighted: false
  },
  {
    name: "Pro",
    description: "Para times em crescimento",
    price: "R$ 49",
    priceDetail: "/mes por usuario",
    features: [
      "Projetos ilimitados",
      "100GB de armazenamento",
      "Suporte prioritario",
      "Analytics avancado",
      "Integracao com APIs",
      "SSO e SAML"
    ],
    cta: "Testar 14 dias gratis",
    highlighted: true
  },
  {
    name: "Enterprise",
    description: "Para grandes organizacoes",
    price: "Customizado",
    priceDetail: "contato comercial",
    features: [
      "Tudo do Pro",
      "Armazenamento ilimitado",
      "SLA garantido",
      "Gerente de conta dedicado",
      "Treinamento personalizado",
      "On-premise disponivel"
    ],
    cta: "Falar com vendas",
    highlighted: false
  }
];

export function Pricing() {
  return (
    <section className="py-24 bg-slate-50 dark:bg-slate-900">
      <div className="container mx-auto px-4">
        {/* Header */}
        <div className="max-w-3xl mx-auto text-center mb-16">
          <p className="text-sm font-semibold text-primary mb-3 uppercase tracking-wider">
            Precos
          </p>
          <h2 className="text-3xl sm:text-4xl font-bold text-slate-900 dark:text-white mb-4">
            Planos para cada momento
          </h2>
          <p className="text-lg text-slate-600 dark:text-slate-400">
            Comece gratis e escale conforme sua necessidade.
          </p>
        </div>

        {/* Grid de planos */}
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
          {plans.map((plan, index) => (
            <div
              key={index}
              className={cn(
                "relative p-8 rounded-2xl border transition-all duration-300",
                plan.highlighted
                  ? "border-primary bg-white dark:bg-slate-950 shadow-xl shadow-primary/10 scale-105 z-10"
                  : "border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-950 hover:border-slate-300 dark:hover:border-slate-700"
              )}
            >
              {/* Badge popular */}
              {plan.highlighted && (
                <div className="absolute -top-4 left-1/2 -translate-x-1/2">
                  <span className="px-4 py-1 rounded-full bg-primary text-white text-sm font-medium">
                    Mais popular
                  </span>
                </div>
              )}

              {/* Conteudo do plano */}
              <div className="space-y-6">
                {/* Nome e descricao */}
                <div>
                  <h3 className="text-xl font-bold text-slate-900 dark:text-white">
                    {plan.name}
                  </h3>
                  <p className="text-sm text-slate-600 dark:text-slate-400 mt-1">
                    {plan.description}
                  </p>
                </div>

                {/* Preco */}
                <div className="pb-6 border-b border-slate-200 dark:border-slate-800">
                  <span className="text-4xl font-bold text-slate-900 dark:text-white">
                    {plan.price}
                  </span>
                  <span className="text-slate-600 dark:text-slate-400 ml-2">
                    {plan.priceDetail}
                  </span>
                </div>

                {/* Features */}
                <ul className="space-y-3">
                  {plan.features.map((feature, i) => (
                    <li key={i} className="flex items-start gap-3">
                      <Check className="w-5 h-5 text-primary shrink-0 mt-0.5" />
                      <span className="text-slate-600 dark:text-slate-400">
                        {feature}
                      </span>
                    </li>
                  ))}
                </ul>

                {/* CTA */}
                <Button 
                  className="w-full" 
                  variant={plan.highlighted ? "default" : "outline"}
                  size="lg"
                >
                  {plan.cta}
                </Button>
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}
```

---

## Referencias Uteis

- **Inspiracao**: [Awwwards](https://www.awwwards.com/) - Sites premiados
- **Componentes**: [21st.dev](https://21st.dev/community/components) - Componentes da comunidade
- **UI Kit**: [shadcn/ui](https://ui.shadcn.com/) - Componentes acessiveis
- **Icones**: [Lucide](https://lucide.dev/) - Icones consistentes
- **Cores**: [Tailwind Colors](https://tailwindcss.com/docs/customizing-colors) - Paleta de cores

---

## Checklist de Qualidade

- [ ] Design system definido (cores, tipografia, espacamento)
- [ ] Layout mobile-first implementado
- [ ] Estados interativos (hover, focus, active, disabled)
- [ ] Dark mode suportado
- [ ] Acessibilidade basica (contraste, focus, semantic HTML)
- [ ] Animacoes sutis e performaticas
- [ ] Componentes reutilizaveis
- [ ] Sem hardcode de cores inline
