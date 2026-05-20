# TouchDesigner Generative Particle System

A TouchDesigner project that extends the [GLSL Vertex Displacement](https://github.com/steven-tbd/Touchdesigner-GLSL-vertex-displacement) shader into an animated particle system driven by texture feedback and procedural motion.

This work was reposted by the official TouchDesigner Instagram account.

![TouchDesigner Particle System Animation](particle-animation.gif)

## How It Works

The system uses the same GLSL MAT from the GLSL Vertex Displacement project. The sphere geometry is converted into a particle system via a `Convert SOP`, replacing solid geometry with individual points that the shader displaces.

Before reaching the shader, the source texture passes through a switchable effects module inside `container_fx`. The module includes a feedback loop, a radial blur, and a light tunnel effect. Because the feedback loop feeds the texture's previous state back into itself, the texture's history continuously shapes the particle positions.

An LFO drives the `dispScale` uniform, creating a pulsing animation without keyframes. A second feedback loop on the final rendered output adds temporal blurring and visual echoes.

## Usage

Open the `.toe` file in TouchDesigner. The animation runs automatically. Swap the source image using the `Movie File In TOP` inside `media_input`. Switch between pre-processing effects inside the `container_fx` component.

![TouchDesigner Network](touchdesigner-network.png)

## Links

- [Project Write-up](https://stevenmbenton.com/generative-particle-system/)
