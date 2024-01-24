# github-profile-image
```Python
'''

gitsym.py

1/24/2024

'''
import libvgl as vgl
import naca45 as nc

x, y = nc.get_naca45("4412", 50, nc.spc_cos)
#vgl.util.translate_points(x, y, -1, 0)

ndeg = 20
dpi = 2*3.14159265358979/ndeg

fmm = vgl.FrameManager()
frm = fmm.create(0,0,3,3, vgl.Data(-1.1,1.1,-1.1,1.1))
dev = vgl.DeviceIMG("gitsym.png", fmm.get_gbbox(), 150)

dev.set_device(frm)

for i in range(ndeg):
    dev.polygon(x,y,lcol=vgl.crimson,lthk=0.007,fcol=vgl.YELLOW)    
    x, y = vgl.util.rad_rotation_points(x,y,dpi)
    
dev.close()
```
