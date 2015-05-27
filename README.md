Filters4Processing
==================

Filters4Processing is a growing collection of filters for Processing.

## Usage

```Processing

// Create an image object
PImage  myImage;

// Create a shader object
PShader myFilter; 

void setup() {

  size( 512, 512, P2D );
  
  // Import the image file
  myImage  = loadImage( "texture.jpg" );

  // Import the shader file
  myFilter = loadShader( "shader.glsl" );
  
  // Pass the size of the window to the shader
  myFilter.set("sketchSize", float(width), float(height));

}

void draw() { 

  // Draw the image on the scene
  image( myImage, 0, 0 );

  // Applies the shader to the scene
  filter( myFilter );

}
```

This is a minimal example. Some shaders require additional uniforms. Refer to the comments in the code or publish an issue if something is not working as it should.


## Notes about porting filters from Shadertoy

Here are some useful tips if you want to help extend the library of filters available for Processing.

*Note: It is of course possible to port other types of shaders, but this document focuses on filters.*

Replace:
`void mainImage( out vec4 fragColor, in vec2 fragCoord )` -> `void main( void )`

Replace all:
* `iChannel0` -> `texture`
* `fragCoord` -> `gl_FragCoord`
* `fragColor` -> `gl_FragColor`

There is more to it than this but these tips should cover most basic filters.

Now go dig for [filters on Shadertoy](https://www.shadertoy.com/results?query=filter)!

## License
All shaders from Shadertoy belong to there respective authors. Unless otherwise specified in the shader file, they are licensed under Creative Commons ([CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.en_US))