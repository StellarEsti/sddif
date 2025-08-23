<script lang="ts">
import { defineComponent } from 'vue'
import { VueLatex } from 'vatex'

export default defineComponent({
  components: {
    VueLatex
  }
})
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title" id="Supplementary">Supplementary</h1>
    </el-row>

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
        <p>
        <!-- Thanks to
        <a href="https://katex.org/docs/options.html" target="_blank">KaTex</a>
        and
        <a href="https://github.com/Shimada666/VaTex" target="_blank">VaTex</a>,
        now we can show an inline
        <VueLatex expression="\LaTeX" />
        formula, like
        <VueLatex expression="1+1=2" />.
        And we can show an interline formula like this: 
        <VueLatex expression="
            D(x) = \begin{cases}
            \lim\limits_{x \to 0} \frac{a^x}{b+c}, & x<3 \\
            \pi, & x=3 \\
            \int_a^{3b}x_{ij}+e^2 \mathrm{d}x,& x>3 \\
            \end{cases}
          " display-mode /> -->
            <p><strong>Theorem 1.</strong> <em>Given the directional diffusion process with control signal <VueLatex expression="\bm{u_0}" />, sampling the state <VueLatex expression="{\bm{x}}_t" /> at an arbitrary timestep <VueLatex expression="t"/> are expressed in closed form:</em></p>
        <VueLatex expression="
                 q({{\bm{x}}_t}|{{\bm{x}}_0},{{\bm{u}}_0}) := {\cal N}(\bm{x}_t;\prod_{k = 1}^t {{\alpha _k}} {{\bm{x}}_0} + (1 - \prod_{k = 1}^t {{\alpha _k}} ){{\bm{u}}_0}, \sigma^2_t {\bf{I}})
          " display-mode />
            <p><strong>Proof:</strong> <em>As described in the main text, we formalize the directional diffusion process as follows:</em></p>
        <VueLatex expression="
            q({{\bm{x}}_t}|{{\bm{x}}_{t - 1}},{{\bm{u}}_0}): = {\cal N}({{\bm{x}}_t};{\alpha _t}{{\bm{x}}_{t - 1}} + (1 - {\alpha _t}){{\bm{u}}_0},\lambda _t^2{\bf{I}})
          " display-mode />
            <p><em>For simplicity, the Eqn.2 is represented by <VueLatex expression="{{\bm{x}}_t}: = {\alpha _t}{{\bm{x}}_{t - 1}} + (1 - {\alpha _t}){{\bm{u}}_0} + {\lambda _t}{{\bm{\epsilon }}}" />. The previous latent is iteratively replaced according to Eqn.2</em></p>
        <VueLatex expression="
            \begin{align}
       \boldsymbol{x}_t:&=\alpha _t\boldsymbol{x}_{t-1}+\left( 1-\alpha _t \right) \boldsymbol{u}_0+\lambda _t\boldsymbol{\epsilon }\\
&=\alpha _t\alpha _{t-1}\boldsymbol{x}_{t-2}+\left( 1-\alpha _t\alpha _{t-1} \right) \boldsymbol{u}_0+\sqrt{\lambda _{t}^{2}+\alpha _{t}^{2}\lambda _{t-1}^{2}}\boldsymbol{\epsilon }\\
&=\cdots \\
&=\prod_{i=1}^t{\alpha _i}\boldsymbol{x}_{t-2}+\left( 1-\prod_{i=1}^t{\alpha _i} \right) \boldsymbol{u}_0+\sqrt{\lambda _{t}^{2}+\alpha _{t}^{2}\lambda _{t-1}^{2}+\cdots +\prod_{i=2}^t{\alpha _{i}^{2}}\lambda _{1}^{2}}\boldsymbol{\epsilon }\\
&=\prod_{i=1}^t{\alpha _i}\boldsymbol{x}_{t-2}+\left( 1-\prod_{i=1}^t{\alpha _i} \right) \boldsymbol{u}_0+\sqrt{\sum_{k=1}^t{\bar{\alpha}_{t}^{2}\lambda _{k}^{2}/\bar{\alpha}_{k}^{2}}}\boldsymbol{\epsilon }
   \end{align}
          " display-mode />
          <p><em>The proposition is proven. To prove Theorem 2, we first introduce Lemma 1.<br>
          <strong>Lemma 1.</strong> the directional diffusion process with the radar control signal <VueLatex expression="\bm{u_0}" />, the variational bound on negative log likelihood of the LiDAR's SDDR condition distribution <VueLatex expression="p(\bm{x}_0|\bm{u}_0)" /> is determined by
          
        <VueLatex expression="
            \mathop {\min }\limits_\theta  \sum\limits_{t = 1}^T {\mathbb{E}\left[ {{D_{KL}}\left[ {q\left( {{{\bm{x}}_{t - 1}}|{{\bm{x}}_t},{{\bm{x}}_0},{{\bm{u}}_0}} \right)||{p_\theta }\left( {{{\bm{x}}_{t - 1}}|{{\bm{x}}_t},{{\bm{u}}_0}} \right)} \right]} \right]}
          " display-mode />

        <p><em><strong>Proof:</strong> Given a set of parameterized Markov chain <VueLatex expression="\{\bm{x}_0,\bm{x}_1,\cdots,\bm{x}_T\}" /> and our radar signal <VueLatex expression="\bm{u_0}" /> as a condition, the reverse process  w.r.t. the joint distribution <VueLatex expression="p_{\bm{\theta}}({{\bf{x}}_{0:T}}|{{\bf{u}}_0})" /> of these lantent variables is expressed by 
            <VueLatex expression="
            \begin{equation}
                    \begin{aligned}
              p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_{0:T}|\boldsymbol{u}_0 \right) &=p\left( \boldsymbol{x}_{1:T}|\boldsymbol{u}_0 \right) p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_0|\boldsymbol{x}_{1:T},\boldsymbol{u}_0 \right)\\
              &=p\left( \boldsymbol{x}_{1:T}|\boldsymbol{u}_0 \right) p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_0|\boldsymbol{x}_1,\boldsymbol{u}_0 \right)\\
              &=p\left( \boldsymbol{x}_{2:T}|\boldsymbol{u}_0 \right) p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_1|\boldsymbol{x}_2,\boldsymbol{u}_0 \right) p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_0|\boldsymbol{x}_1,\boldsymbol{u}_0 \right)\\
              &=p\left( \boldsymbol{x}_T|\boldsymbol{u}_0 \right) \prod\limits_{t=1}^T{p_{\boldsymbol{\theta }}}\left( \boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{u}_0 \right)\\
                    \end{aligned}
                \end{equation}          
            " display-mode />
        Therefore, we can explicitly express the target distribution through the accumulated joint distribution as follows:
          <VueLatex expression="
            \begin{align}
            p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_0|\boldsymbol{u}_0 \right) &=\int{p\left( \boldsymbol{x}_{0:T}|\boldsymbol{u}_0 \right) \text{d}\boldsymbol{x}_{1:T}}\\
            &=\int{p\left( \boldsymbol{x}_T|\boldsymbol{u}_0 \right) \prod\limits_{t=1}^T{p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{u}_0 \right) \text{d}\boldsymbol{x}_{1:T}}},
            \end{align}   
            " display-mode />
        Therefore, the evidence lower bound (ELBO) of the target distribution given the radar's SDDR is expressed as
          <VueLatex expression="
            \begin{align}
            \bm{L}&=\left[ -\log p_{\theta}\left( \bm{x}_0|\bm{u}_0 \right) \right] \\
            &=\left[ -\log \int{p_{\theta}}\left( \bm{x}_{0:T}|\bm{u}_0 \right) d\bm{x}_{1:T} \right] \\
            &=\left[ -\log \int{\frac{p_{\theta}\left( \bm{x}_{0:T}|\bm{u}_0 \right) q\left( \bm{x}_{1:T}|\bm{x}_0,\bm{u}_0 \right)}{q\left( \bm{x}_{1:T}|\bm{x}_0,\bm{u}_0 \right)}}d\bm{x}_{1:T} \right] \\
            &=-\log \mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \frac{p_{\theta}\left( \bm{x}_{0:T}|\bm{u}_0 \right)}{q\left( \bm{x}_{1:T}|\bm{x}_0,\bm{u}_0 \right)} \right] \\
            &\le -\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p_{\theta}\left( \bm{x}_{0:T}|\bm{u}_0 \right)}{q\left( \bm{x}_{1:T}|\bm{x}_0,\bm{u}_0 \right)} \right] \\
            &=\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ -\log \frac{p\left( \bm{x}_T|\bm{u}_0 \right) \prod\limits_{t=1}^T{p_{\theta}}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right)}{\prod\limits_{t=1}^T{q}\left( \bm{x}_t|\bm{x}_{t-1},\bm{u}_0 \right)} \right] \\
            &=-\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p\left( \bm{x}_T|\bm{u}_0 \right) p_{\theta}\left( \bm{x}_0|\bm{x}_1,\bm{u}_0 \right)}{q\left( \bm{x}_1|\bm{x}_0,\bm{u}_0 \right)} \right] -\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \prod\limits_{t=2}^T{\frac{p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right)}{q\left( \bm{x}_t|\bm{x}_{t-1},\bm{u}_0 \right)}} \right] \\
            &=-\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p\left( \bm{x}_T|\bm{u}_0 \right) p_{\theta}\left( \bm{x}_0|\bm{x}_1,\bm{u}_0 \right)}{q\left( \bm{x}_1|\bm{x}_0,\bm{u}_0 \right)} \right] -=\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \prod\limits_{t=2}^T{\frac{p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right)}{q\left( \bm{x}_t|\bm{x}_{t-1},\bm{x}_0,\bm{u}_0 \right)}} \right] \\
            &=-\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p\left( \bm{x}_T|\bm{u}_0 \right) p_{\theta}\left( \bm{x}_0|\bm{x}_1,\bm{u}_0 \right)}{q\left( \bm{x}_1|\bm{x}_0,\bm{u}_0 \right)} \right] -\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \prod\limits_{t=2}^T{\frac{p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right) q\left( \bm{x}_{t-1}|\bm{x}_0,\bm{u}_0 \right)}{q\left( \bm{x}_{t-1}|\bm{x}_t,\bm{x}_0,\bm{u}_0 \right) q\left( \bm{x}_t|\bm{x}_0,\bm{u}_0 \right)}} \right] \\
            &=-\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p\left( \bm{x}_T|\bm{u}_0 \right) p_{\theta}\left( \bm{x}_0|\bm{x}_1,\bm{u}_0 \right)}{q\left( \bm{x}_1|\bm{x}_0,\bm{u}_0 \right)}+\log \frac{q\left( \bm{x}_1|\bm{x}_0,\bm{u}_0 \right)}{q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right)}+\log \prod\limits_{t=2}^T{\frac{p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right)}{q\left( \bm{x}_{t-1}|\bm{x}_t,\bm{x}_0,\bm{u}_0 \right)}} \right] \\
            &=-\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p\left( \bm{x}_T|\bm{u}_0 \right) p_{\theta}\left( \bm{x}_0|\bm{x}_1,\bm{u}_0 \right)}{q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right)}+\log \prod\limits_{t=2}^T{\frac{p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right)}{q\left( \bm{x}_{t-1}|\bm{x}_t,\bm{x}_0,\bm{u}_0 \right)}} \right] \\
            &=-\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \frac{p\left( \bm{x}_T|\bm{u}_0 \right)}{q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right)} \right] -\mathbb{E}_{q\left( \bm{x}_{1:T}|\bm{x}_0 \right)}\left[ \log \prod\limits_{t=1}^T{\frac{p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right)}{q\left( \bm{x}_{t-1}|\bm{x}_t,\bm{x}_0,\bm{u}_0 \right)}} \right] \\
            &=D_{KL}\left[ q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right) ||\frac{p\left( \bm{x}_T|\bm{u}_0 \right)}{q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right)} \right] +\sum\limits_{t=1}^T{\mathbb{E}_{q\left( \bm{x}_t|\bm{x}_0 \right)}\left[ D_{KL}\left[ q\left( \bm{x}_{t-1}|\bm{x}_t,\bm{x}_0,\bm{u}_0 \right) ||p_{\theta}\left( \bm{x}_{t-1}|\bm{x}_t,\bm{u}_0 \right) \right] \right]}
            \end{align}
            " display-mode />
        Based on the known fact of the forward process, the first item <VueLatex expression="D_{KL}\left[ q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right) ||\frac{p\left( \bm{x}_T|\bm{u}_0 \right)}{q\left( \bm{x}_T|\bm{x}_0,\bm{u}_0 \right)} \right]" /> in Eqn. 21 is a constant about the posterior distribution <VueLatex expression="p_{\boldsymbol{\theta }}\left( \boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{u}_0 \right) 
        " />. Therefore, we can simplify <VueLatex expression="\bm{L}" /> by optimizing the following:
          <VueLatex expression="
                \begin{align}
            \mathop {\min }\limits_\theta  \sum\limits_{t = 1}^T {\mathbb{E}\left[ {{D_{KL}}\left[ {q\left( {{{\bm{x}}_{t - 1}}|{{\bm{x}}_t},{{\bm{x}}_0},{{\bm{u}}_0}} \right)||{p_\theta }\left( {{{\bm{x}}_{t - 1}}|{{\bm{x}}_t},{{\bm{u}}_0}} \right)} \right]} \right]}
            \end{align}
            " display-mode />
        The proposition is proven. <br>
        <strong>Theorem 2. </strong> For directional diffusion, with the forward process defined in Eqn. 2, the posterior distribution of the latent variable is tractable when conditioned on <VueLatex expression="\bm{x_0}" /> and radar's prior <VueLatex expression="\bm{u_0}" />, and is given in explicit form as follows:
          <VueLatex expression="
            \begin{equation}
              % \begin{aligned}
          p\left( \boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0,\boldsymbol{u}_0 \right) \propto \exp \left( -\frac{\left( \boldsymbol{x}_{t-1}-\boldsymbol{ \tilde{\mu}_t  } (\bm{x}_{0,t},\bm{u}_0) \right) ^2}{2\sigma_t ^2} \right) 
          % \end{aligned}
          \end{equation}
            " display-mode />
          <VueLatex expression="
            \begin{equation}
           \begin{aligned}
            \text{where\ } \boldsymbol{\tilde{\mu}_t }=\frac{\alpha _t\beta _{t-1}^{2}}{\beta _{t}^{2}}\boldsymbol{x}_t+\frac{\beta _{t}^{2}-\alpha _t\beta _{t-1}^{2}-\lambda _{t}^{2}\bar{\alpha}_{t-1}}{\beta _{t}^{2}}\boldsymbol{u}_0+{\lambda _{t}^{2}\bar{\alpha}_{t-1}}\boldsymbol{x}_0/{\beta _{t}^{2}} \quad \text{and} \quad \sigma_t ^2=\lambda _{t}^{2}\beta _{t-1}^{2}/\beta _{t}^{2}\\
            \end{aligned}
          \end{equation}
            " display-mode />

        <strong>Proof. </strong> Based on Lemma 1, we deduce that the target of the SDDR purification is to minimize the distance between the distribution <VueLatex expression="q\left( {{{\bm{x}}_{t - 1}}|{{\bm{x}}_t},{{\bm{x}}_0},{{\bm{u}}_0}} \right)"/> and the parameterized posterior distribution <VueLatex expression="{p_\theta }\left( {{{\bm{x}}_{t - 1}}|{{\bm{x}}_t},{{\bm{u}}_0}} \right)"/>. By applying Bayes' theorem, we obtain:
          <VueLatex expression="
            \begin{align}
                      q\left( \bm{x}_{t-1}|\bm{x}_t,\bm{x}_0,\bm{u}_0 \right) &=\frac{q\left( \bm{x}_t|\bm{x}_{t-1},\bm{x}_0,\bm{u}_0 \right) q\left( \bm{x}_{t-1}|\bm{x}_0,\bm{u}_0 \right)}{q\left( \bm{x}_t|\bm{x}_0,\bm{u}_0 \right)}\\
            &=\frac{q\left( \bm{x}_t|\bm{x}_{t-1},\bm{u}_0 \right) q\left( \bm{x}_{t-1}|\bm{x}_0,\bm{u}_0 \right)}{q\left( \bm{x}_t|\bm{x}_0,\bm{u}_0 \right)}
          \end{align}
            " display-mode />
        Considering the forward process <VueLatex expression="q\left( \bm{x}_t|\bm{x}_{t-1},\bm{x}_0,\bm{u}_0 \right)\sim 
        \mathcal{N}\left( \bm{x}_t;\alpha _t\bm{x}_{t-1}+\left( 1-\alpha _t \right) \bm{u}_0,\lambda _{t}^{2}\bm{I} \right) 
        "/>, arbitrary sampling distribution <VueLatex expression="q\left( \bm{x}_{t-1}|\bm{x}_0,\bm{u}_0 \right)\sim \mathcal{N}\left( \bm{x}_{t-1};\bar{\alpha}_{t-1}\bm{x}_0+\left( 1-\bar{\alpha}_{t-1} \right) \bm{u}_0,\sum\limits_{k=1}^{t-1}{\frac{\bar{\alpha}_{t-1}^{2}}{\bar{\alpha}_{k}^{2}}\lambda _{k}^{2}}\bm{I} \right) 
        "/>, and the distribution of sampling state at timestamp <VueLatex expression="t"/>, <VueLatex expression="q\left( \bm{x}_t|\bm{x}_0,\bm{u}_0 \right)\sim 
        \mathcal{N}\left( \bm{x}_t;\bar{\alpha}_t\bm{x}_0+\left( 1-\bar{\alpha}_t \right) \bm{u}_0,\sum\limits_{k=1}^t{\frac{\bar{\alpha}_{t}^{2}}{\bar{\alpha}_{k}^{2}}\lambda _{k}^{2}}\bm{I} \right) 
        "/>, the distribution given the next latent SDDR <VueLatex expression="\bm{x}_t"/>, LiDAR's SDDR and conditional signal <VueLatex expression="\bm{u}_0"/> from the radar is expressed as
          <VueLatex expression="
            \begin{align}
            q\left( \boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0,\boldsymbol{u}_0 \right) &\propto \exp ( -\frac{\left( \bm{x}_t-\alpha _t\bm{x}_{t-1}-\left( 1-\alpha _t \right) \bm{u}_0 \right) ^2}{2\lambda _{t}^{2}}-\frac{\left( \bm{x}_{t-1}-\bar{\alpha}_{t-1}\bm{x}_0-\left( 1-\bar{\alpha}_{t-1} \right) \bm{u}_0 \right) ^2}{2\sum\limits_{k=1}^{t-1}{\frac{\bar{\alpha}_{t-1}^{2}}{\bar{\alpha}_{k}^{2}}\lambda _{k}^{2}}}\\
              &+\frac{\left( \bm{x}_t-\bar{\alpha}_t\bm{x}_0-\left( 1-\bar{\alpha}_t \right) \bm{u}_0 \right) ^2}{2\sum\limits_{k=1}^t{\frac{\bar{\alpha}_{t}^{2}}{\bar{\alpha}_{k}^{2}}\lambda _{k}^{2}}} ) \\
              &=\exp ( -\frac{1}{2}[ \frac{\left( \bm{x}_t-\alpha _t\bm{x}_{t-1}-\left( 1-\alpha _t \right) \bm{u}_0 \right) ^2}{\lambda _{t}^{2}}+\frac{\left( \bm{x}_{t-1}-\bar{\alpha}_{t-1}\bm{x}_0-\left( 1-\bar{\alpha}_{t-1} \right) \bm{u}_0 \right) ^2}{\beta _{t-1}^{2}}\\
              &-\frac{\left( \bm{x}_t-\bar{\alpha}_t\bm{x}_0-\left( 1-\bar{\alpha}_t \right) \bm{u}_0 \right) ^2}{\beta _{t}^{2}} ] ) \\
              &\propto \exp \left( -\frac{1}{2}\frac{\left( \bm{x}_{t-1}-\left( \frac{\alpha _t\beta _{t-1}^{2}}{\beta _{t}^{2}}\bm{x}_t+\frac{\beta _{t}^{2}-\alpha _t\beta _{t-1}^{2}-\lambda _{t}^{2}\bar{\alpha}_{t-1}}{\beta _{t}^{2}}\bm{u}_0+\frac{\lambda _{t}^{2}\bar{\alpha}_{t-1}}{\beta _{t}^{2}}\bm{x}_0 \right) \right) ^2}{\frac{\lambda _{t}^{2}\beta _{t-1}^{2}}{\beta _{t}^{2}}} \right) 
          \end{align}
            " display-mode />
        The proposition is proven.
        </em></p>
        <h2>Analysis of Doppler-Consistency</h2>
        <div style="text-align: center;">
        <img src="/doppler.png" alt="Doppler"  width="600">
        </div>
        As the above Fig. shows, the Doppler-Consistency bridges Spatial and Doppler features of the radar. As described in the main text, Doppler velocity, i.e. relative radial velocity <VueLatex expression="
        v_{i,j}^{r}"/>, is typically determined by the radar's ego-velocity <VueLatex expression="\bm{v}^{ego}"/> and the target's azimuth <VueLatex expression="a_i"/> and elevation angle <VueLatex expression="e_j"/>
          <VueLatex expression="
        \begin{equation}
            v_{i,j}^{r}=\left[ \cos a_i\cos e_j,\sin a_i\cos e_j,\sin e_j \right] \left[ v_{x}^{ego},v_{y}^{ego},v_{z}^{ego} \right] ^T
        \end{equation}
          " display-mode />

        According to the Cauchy-Schwarz inequality, we can derive the upper bound of the Doppler velocity.
          <VueLatex expression="
        \begin{align}
        v_{i,j}^{r}&=\left[ \cos a_i\cos e_j,\sin a_i\cos e_j,\sin e_j \right] \left[ v_{x}^{ego},v_{y}^{ego},v_{z}^{ego} \right] ^T\\
        &\leq \sqrt{\left( \cos a_i\cos e_j \right) ^2+\left( \sin a_i\cos e_j \right) ^2+\left( \sin e_j \right) ^2}\cdot \sqrt{\left( v_{x}^{ego} \right) ^2+\left( v_{z}^{ego} \right) ^2+\left( v_{z}^{ego} \right) ^2}\\ 
        &=\sqrt{\left( \cos e_j \right) ^2+\left( \sin e_j \right) ^2}\lVert \boldsymbol{v}^{ego} \rVert _2\\
        &=\lVert \boldsymbol{v}^{ego} \rVert _2
        \end{align}
            " display-mode />

        Equality 35 holds if and only if object's spatial direction vector <VueLatex expression="\left[ \cos a_i\cos e_j,\sin a_i\cos e_j,\sin e_j \right]"/> is collinear with the radar's ego velocity vector <VueLatex expression="\boldsymbol{v}^{ego}"/>. As shown in Fig. 1, this means the peak height of the distribution surface of <VueLatex expression="v^{r}"/> w.r.t. <VueLatex expression="a_i"/> and <VueLatex expression="e_j"/> corresponds to the magnitude of the radar's velocity, while the peak position indicates the azimuth and elevation angles of the radar's motion.

          </em></p>

        
        
        </p>
      </el-col>
    </el-row>
  </div>


  <div>
  <el-divider />
  <el-row justify="center">
      <h1 class="section-title" id="ResultTable">Results</h1>
      
    </el-row>
  <div style="text-align: center;">
        <img src="/pce_result.png" alt="pce_result"  width="1200">
        <img src="/eve_result.png" alt="pce_result"  width="800"><br>

        <img src="/reliability.png" alt="pce_result"  width="800">

        </div>
  </div>
</template>

<style scoped>

</style>