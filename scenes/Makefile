.PHONY : all

#n.b. the '-y' sets autoexec scripts to 'on' so that driver expressions will work
UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Darwin)
	BLENDER = /Applications/Blender/blender.app/Contents/MacOS/blender -y
else ifeq ($(UNAME_S),Linux)
	BLENDER = ../../blender-2.90.0-linux64/blender -y
else
	BLENDER = blender
endif

EXPORT_MESHES=export-meshes.py
EXPORT_WALKMESHES=export-walkmeshes.py
EXPORT_SCENE=export-scene.py

DIST=../dist

all : \
	$(DIST)/mygame.pnct \
	$(DIST)/mygame.w \
	$(DIST)/mygame.scene \

$(DIST)/mygame.pnct : mygame.blend $(EXPORT_MESHES)
	blender --background --python $(EXPORT_MESHES) -- '$<':Platforms '$@'

$(DIST)/mygame.scene : mygame.blend $(EXPORT_SCENE)
	blender --background --python $(EXPORT_SCENE) -- '$<':Platforms '$@'

$(DIST)/mygame.w : mygame.blend $(EXPORT_WALKMESHES)
	blender --background --python $(EXPORT_WALKMESHES) -- '$<':WalkMeshes '$@'
