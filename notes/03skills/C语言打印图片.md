# C语言打印图片

## 图片格式为ppm

```C
#include <iostream>
#include <cmath>
#include <cstdlib>

#define DIM 1024

void pixel_write(int,int);
FILE *fp;

int main()
{
	fp = fopen("black_white_image.ppm","wb");
	if (!fp)
	{
		return -1;
	}

	fprintf(fp, "P6\n%d %d\n255\n", DIM, DIM);
	for(int j=0;j<DIM;j++)
	{
		for(int i=0;i<DIM;i++)
		{
			pixel_write(i,j);
		}
	}
	fclose(fp);

	return 0;
}

void pixel_write(int i, int j)
{
	static unsigned char color[3];

	float x = i/(DIM - 1.0f);
	float y = j/(DIM - 1.0f);

	float k = powf(2.0f, ceilf(y * 8.0f)) * x / 2.0f;
	k = k - floorf(k);
	if (k > 0.5f)
	{
		color[0] = color[1] = color[2] = 255;
	}
	else
	{
		color[0] = color[1] = color[2] = 0;
	}

	fwrite(color, 1, 3, fp);
}
```

